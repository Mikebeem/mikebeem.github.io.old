---
layout: post
title:  "Blog With GitHub Pages"
date:   2022-01-14 07:13:40 +0100
categories: blogging, GitHub
---

Well, my first personal blog is about writing a blog ;). It is not about how to write a blog in general, but how to build your blog with GitHub Pages. 

I had this idea to start blogging about the things I experience during my work. In my daily work as DevOps Consultant, I help other companies and teams with improving the way they work and the tools they use. During my work, I'm using Azure DevOps a lot, I also write a lot of PowerShell scripts. As Microsoft is focussing more on GitHub, I also decided to learn more of GitHub myself. I do use GitHub already, but mostly in the Code and Issues sections. So when I found out that I can write and host my blog in GitHub, I wanted to give it a try.

So with GitHub Pages, you are able to turn a repository hosted in GitHUb into a website. By default, you just need to add some HTML files to your repo, and GitHub serves your website. In this blog, I'm also using Jekkyl. This is an open source tool that transforms plain text into websites. So you only need to write markdown files and Jekkyl and GitHub will make a nice website for you. Configuration is done in YAML, so it sounds like a perfect match for me.

So I started ith creating a new repository in GitHub, with the name: mikebeem.github.io. The name of this repository needs to be in this format: <username>.github.io. 

After that, I just followed the simple steps described and created my first "Hello World" page.

At the bottom of the page, I found that big URL saying: "Blogging with Jekyll". So I installed the most recent Ruby version from https://rubyinstaller.org/downloads/ and after that i ran "gem install jekyll bundler".

I deleted all files from the root and from the root of my new repositroy, I ran {% highlight Bash %}jekyll new --skip-bundle .{% endhighlight %} to create new Jekyll site. If you don't want to empty your folder, you can add --force to the command line.

I edited the Gemfile file, commented out the  gem "jekyll" line, uncommented the gem "github-pages" line and edited like described: "gem "github-pages", "~> 219", group: :jekyll_plugins". As 219 is the  version at this moment: https://pages.github.com/versions/

After saving the file, I ran {% highlight Bash %}bundle install{% endhighlight %}. I wanted to see what the new site looks like without publishing directly. I followed the steps from GitHub Pages: {% highlight Bash %}bundle exec jekyll serve{% endhighlight %}

But that gave me the error: 

{% highlight command %}
C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve/servlet.rb:3:in `require': cannot load such file -- webrick (LoadError)
from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve/servlet.rb:3:in `<top (required)>'
from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve.rb:184:in `require_relative'
from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve.rb:184:in `setup'
from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve.rb:102:in `process'
from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve.rb:93:in `block in start'
from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve.rb:93:in `each'
from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve.rb:93:in `start'
from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve.rb:75:in `block (2 levels) in init_with_program'
from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/mercenary-0.3.6/lib/mercenary/command.rb:220:in `block in execute'
from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/mercenary-0.3.6/lib/mercenary/command.rb:220:in `each'
from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/mercenary-0.3.6/lib/mercenary/command.rb:220:in `execute'
from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/mercenary-0.3.6/lib/mercenary/program.rb:42:in `go'
from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/mercenary-0.3.6/lib/mercenary.rb:19:in `program'
from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-3.9.0/exe/jekyll:15:in `<top (required)>'
from C:/Ruby31-x64/bin/jekyll:25:in `load'
from C:/Ruby31-x64/bin/jekyll:25:in `<main>'
{% endhighlight %}

So I found some similar issues on Google and ran: bundle add webrick.
To prevent this in the future, I also added gem "webrick" to my Gemfile.

After that, I was able to test my website with: {% highlight Bash %}bundle exec jekyll serve {% endhighlight %}

![Server is running!](/assets/images/server-running.png)

So now I'm able to test my new webiste at http://localhost:4000. And yeah, it works!

![Site is up!](/assets/images/site-is-up.png)

Well, it's all still basic, but I kinda expected that because I didn't change anything yet. So I made some changes to persanolize the site a little bit. 

So I went over to the config file: _config.yml and made changes to the Post that was already created by Jekyll. And made some changes. After saving the files, the site is regenerated and the changes are visible directly. Well, exept for changes in the _config.yml, for those changes you need to stop the serve and start it again.