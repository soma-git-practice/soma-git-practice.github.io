# be rake posts:new
namespace :posts do
  desc "新しい投稿を作成します。"
  task :new do |task|
    input = {}

    puts "新しい投稿を作成します。情報を入力してください。"
    print "タイトル："
    input[:title] = STDIN.gets.strip
    if input[:title].length == 0
      puts "タイトルは1文字以上入力してください。"
      next
    end
    
    print "概要："
    input[:overview] = STDIN.gets.strip
    if input[:overview].length == 0
      puts "概要は1文字以上入力してください。"
      next
    end

    print "カテゴリ："
    input[:category] = STDIN.gets.strip
    if input[:category].length == 0
      puts "カテゴリは1文字以上入力してください。"
      next
    end

    puts "以下の内容で投稿を作成していいですか？(Y/n)"
    puts input.inspect

    unless STDIN.gets.strip.downcase == 'y'
      puts "キャンセルしました。"
      next
    end

    now = Time.now
    filepath = "#{input[:category]}/_posts/#{now.strftime("%Y-%m-%d")}-#{input[:title]}.md"
    puts "ファイルを作成します。 #{filepath}"
    File.open(filepath, 'w') do |f|
      f.write(<<"POST"
---
layout: post
overview:  #{input[:overview]}
---


POST
      )
    end
    puts "ファイルを作成しました。 #{filepath}"
  end
end