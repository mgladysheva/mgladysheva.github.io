---
layout: post
title: Welcoming Post
excerpt: "Welcoming post with no real purpose"
tags: [welcome, code]
modified: 2016-03-05
comments: true
share: true
---

Welcome!

### CODE HIGHLIGHTING TEST

{% highlight ruby %}
#!/usr/bin/env ruby
require 'rubygems'
require 'rest_client'
require 'json'

ids_list_file = ARGV[0]

template = open(ARGV[1]).read

method = ARGV[2]

url = ARGV[3]

errors = File.new("errors.log", "w+")

IO.foreach(ids_list_file) do |id|

  begin
    # we treat every line as user id
    id = id.strip

    query = template.sub('USER_ID_VARIABLE', id) #todo work with template more carefully

    RestClient::Request.execute(method: method, url: url, payload: query, headers: {content_type: 'application/json'})

  rescue

    errors.write("Failed to do requested action for " + id + "\n")

    next

  end

end

errors.close
{% endhighlight %}


### GITHUB GIST TEST

{% gist dgladyshev/6b4566f1fa94af6c0f69 %}
