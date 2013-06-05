require 'rubygems'
require 'optparse'
require 'yaml'

task :post do
  OptionParser.new.parse!
  ARGV.shift
  title = ARGV.join(' ')

  path = "_posts/#{Date.today}-#{title.downcase.gsub(/[^[:alnum:]]+/, '-')}.markdown"
  
  if File.exist?(path)
    puts "[WARN] File exists - skipping create"
  else
    File.open(path, "w") do |file|
      file.puts YAML.dump({'layout' => 'post', 'title' => title, 'date' => Time.now, 'published' => false })
      file.puts "---"
    end
  end
  `open #{path}`

  exit 1
end