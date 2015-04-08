require 'date'
require 'time'

desc 'create a new draft post'
task :post do 
  title = ENV['title']
  slug = "/_posts/#{Date.today}-#{title.downcase.gsub(/[^\w]+/, '-')}"

  file = File.join(
    File.dirname(__FILE__), 
    slug + '.markdown'
  )

  File.open(file, "w") do |f|
    f << <<-EOS.gsub(/^    /, '')
    ---
    layout: post
    title: #{title}
    date: #{Time.now}
    categories:
    ---

    EOS
  end

  system ("#{ENV['EDITOR']} #{file}")
end