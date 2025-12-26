---
layout: post
title:  "Intro to Roda (Ruby web framework) Episode 2"
date:   2025-12-26 00:46:03 +0100
categories: ruby-tools
---

My first feature is a simple Wikipedia search. (If you're wondering what the point is, please try [NINI][nini] or refer to [this post][nini-post].)

It's a simple form with not even a POST request, since there is nothing confidential to the search query terms, and sometimes it can be convenient to bookmark the URL of a search results page. So a GET request should do the job. The corresponding block looks like this:

```ruby
# GET /search request
    r.get "search" do
      if r.params["query"]
        search = WikipediaSearch.new(r.params["query"])
        @search_info = search.search_info
        @results = search.results
        puts "Search info: #{@search_info.inspect}"
        puts "Results: #{@results.inspect}"
        puts r.params["query"].inspect
      end
      view("search")
    end
```
If there are query parameters in the GET request to the `/search` route, these will be searched on Wikipedia thanks to their API (see below) and returned in a convenient format within the `"search"` view.

For the actual Wikipedia search, I have prepared a feature where users will be able to choose among the 334 languages that are offered, but I haven't implemented it yet. You can still see the planned logic of that in the following:
```ruby
require "mediawiki_api"
require "wikipedia-client"
require_relative "language_codes"

class WikipediaSearch
  private

  attr_writer :url, :search_terms, :found_titles

  def initialize(search_terms, language = "English")
    self.url = WIKIPEDIA_LANGUAGES[language.to_sym] + ".wikipedia.org"
    self.search_terms = search_terms
    self.found_titles = search
  end

  def search
    client = MediawikiApi::Client.new("https://" + url + "/w/api.php")
    response = client.action :query, list: "search", srsearch: search_terms, srlimit: 5, srprop: "titlesnippet"
    response.data["search"].map { |page| page["title"] }
  end

  public

  attr_reader :url, :search_terms, :found_titles

  def search_info
    "Your search for \"#{search_terms}\" has returned these #{found_titles.length} possible answers. If these are not the droids you are looking for, please try again with more specific search terms."
  end

  def results
    wikipedia_config = Wikipedia::Configuration.new(domain: url)
    client = Wikipedia::Client.new(wikipedia_config)
    found_titles.map do |title|
        page = client.find(title)
        [ page.title, page.fullurl, page.summary ]
      end
  end
end
```

So far, setting up a GET route with Roda was quite similar to my experience with Bottle (Python) or Sinatra (Ruby). The branching tree-like feature of Roda isn't needed yet, as it shall be in Episode 3, where I'll need successive POST requests to build a haiku.

[NINI]: https://anbarto.pythonanywhere.com
[nini-post]: /projects/2025/11/09/nini-natural-intelligence/

