---
layout: default
title: MarkDown 测试页面了
---
#This should be a H1 header
## 然后这里是二级标题

{% highlight ruby %}
#!/usr/bin/env ruby

require 'json'
require 'net/http'
require 'libnotify'

def parsejson
    file = "http://api.openweathermap.org/data/2.5/find?q=London&mode=json"
    response = Net::HTTP.get_response(URI.parse(file))
    weatherjson = response.body
    actual = JSON.parse(weatherjson)

    # check for errors
    if actual.has_key? 'Error'
        raise "error with the url"
    end

    results = []

    actual["list"].each do |listitem|
        weather = listitem["weather"]
        weather.each do |weath|
            results.push(weath["description"])
        end
        main = listitem["main"]
        temp = main["temp"] - 273.15
        results.push ("%.2f" % temp)
    end

    return results
end
{% endhighlight %}

```
function () {
  console.log("bla");
}

var foo = "bar";
//这里是代码段喽

```

`simple code snippet` 也是必须的功能呀
