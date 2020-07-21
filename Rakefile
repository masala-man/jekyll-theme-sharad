#################################################################
# Modified from https://github.com/mkchoi212/paper-jekyll-theme #
#################################################################

require 'yaml'
#
## Customize post location and post extensions
#
SOURCE = "."
CONF_FILE = YAML.load(File.read('_config.yml'))
CONFIG = {
	'posts' => File.join(SOURCE, "_posts"),
	'post_ext' => "md",
	'theme_package_version' => "1.0",
	'default_cover' => CONF_FILE['cover'],
	'default_author' => CONF_FILE['author']
}

module Colors
	def colorize(text, color_code)
		"\033[#{color_code}m#{text}\033[0m"
	end

	{
		:black    => 30,
		:red      => 31,
		:green    => 32,
		:yellow   => 33,
		:blue     => 34,
		:cyan     => 36,
	}.each do |key, color_code|
		define_method key do |text|
			colorize(text, color_code)
		end
	end
end
include Colors

#
## Just typing `rake` will invoke `rake preview`
#
task :default => :preview
load '_rake-configuration.rb' if File.exist?('_rake-configuration.rb')

desc 'Preview with livereload on local machine'
task :preview do
	puts green "Starting livereload server"
	jekyll('serve')
end
task :serve => :preview

desc 'Clean up generated site'
task :clean do
    cleanup
end

# Usage: rake post title="A Title" [date="2012-02-09"] [tags=[tag1,tag2]] [category="category"]
desc "Begin a new post in #{CONFIG['posts']}"
task :post do
	abort("rake aborted: '#{CONFIG['posts']}' directory not found.") unless FileTest.directory?(CONFIG['posts'])
	title = ENV["title"] || "new-post"
	tags = ENV["tags"] || ""
	cover = ENV["cover"] || "#{CONFIG['default_cover']}"
	cover = "\"#{cover.gsub(/-/,' ')}\"" if !cover.empty?
	author = ENV["author"] || "#{CONFIG['default_author']}"
	author = "\"#{author.gsub(/-/,' ')}\"" if !author.empty?
	slug = title.downcase.strip.gsub(' ', '-').gsub(/[^\w-]/, '')

	begin
		date = (ENV['date'] ? Time.parse(ENV['date']) : Time.now).strftime('%Y-%m-%d')
	rescue => e
		puts red "Error - date format must be YYYY-MM-DD, please check you typed it correctly!"
		exit -1
	end
	filename = File.join(CONFIG['posts'], "#{date}-#{slug}.#{CONFIG['post_ext']}")
	if File.exist?(filename)
		abort("rake aborted!") if ask("#{filename} already exists. Do you want to overwrite?", ['y', 'n']) == 'n'
	end
	
	puts cyan "Creating new post: #{filename}"
	open(filename, 'w') do |post|
		post.puts "---"
		post.puts "layout: coverpost"
		post.puts "title: \"#{title.gsub(/-/,' ')}\""
		post.puts "description: \"\""
		post.puts "date: #{date}"
		post.puts "author: #{author}"
		post.puts "tags: #{tags}"
		post.puts "cover: #{cover}"
		post.puts "---"
	end
	puts cyan "Creating asset directory: .assets/post/#{date}-#{slug}"
	sh "mkdir assets\\post\\#{date}-#{slug}", verbose: false
end # task :post

#
## General support functions
#

def cleanup
	sh 'del /F /Q .\_site\*'
	# sh 'rm -rf ./_site'
end

def jekyll(directives = '')
	sh 'jekyll ' + directives
end

