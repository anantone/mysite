---
layout: post
title:  "Intro to Roda, Episode 3"
date:   2025-12-26 21:12:03 +0100
categories: ruby-tools
---
My second feature is a miniature writing workshop where _you_, the user, are invited to write a haiku. A haiku is a short poem in three verses of 5, 7, 5 syllables, modeled on a traditional Japanese poetical form (which included more constraints, including thematic ones). 

This will get us started with "branching" multiple GET and POST requests, as well as writing the finished haikus to a SQLite database for the purpose of archiving them (the full NINI app offers the option to have one's haiku included in an online anthology, accessible only to those who contribute one haiku)(please see the finished [Python version][python-nini] if you can't wait until all the features are recreated in Ruby/Roda).

Starting with the branching, we first create a branch with `r.on`. Our first page is a simple GET request, as the first prompt is given to users.

```ruby
# GENIE branch
    r.on "genie" do

      r.get "1" do
        view("genie1")
      end
```

In this first view, a form allows the user to submit their first verse. Now we have a POST request!

```ruby
r.post "1" do
        if r.params["verse1"] != ''
          if syllable_count(r.params["verse1"], 5)
            @haiku = Haiku.create(verse1: r.params["verse1"])
            r.session["haiku_id"] = @haiku.id
            r.redirect "/genie/2"
          else
            flash[:info] = HAIKU_COUNT
            r.redirect "/genie/1"
          end
        else
          flash[:error] = "Please enter your first verse to continue."
            r.redirect "/genie/1"
        end
end
```

There are two ways to get an error here:
1) enter nothing and click next.
2) mess up the syllable count (or hitting one of the edge cases that are sure to exist, in which the `ruby_rhymes` gem will be wrong)

In the second case, you will get an "information" message only, blue not red, just to be kind in case you suck at counting to five on your fingers. (We've all been there.) The constant `HAIKU_COUNT` contains a nice message inviting you to try again.

Those messages will flash while you are redirected to the same page. 

Otherwise, if the function `syllable_count` returns true (meaning the `ruby_rhymes` gem agrees with you on the syllable count of the text that you entered), an entry will be created in the database for your haiku, and the first verse added to it (as well as a primary key `id` and an automatic timestamp). This is assigned to an instance variable `@haiku` and `@haiku.id` passed into the session, so that we can add your second verse to the correct first verse, and the third to the correct second, and end up with the correct three verses on page 4. 

Here is how it looks:

```ruby
r.get "2" do
        view("genie2")
      end

      r.post "2" do
        if r.params["verse2"] != ''
          if syllable_count(r.params["verse2"], 7)
            @haiku = Haiku[r.session["haiku_id"]]
            @haiku.update(verse2: r.params["verse2"]) if @haiku
            r.redirect "/genie/3"
          else
            flash[:info] = HAIKU_COUNT
            r.redirect "/genie/2"
          end
        else
          flash[:error] = "Please enter your second verse to continue."
          r.redirect "/genie/2"
        end
      end

      r.get "3" do
        view("genie3")
      end
 
      r.post "3" do
        if r.params["verse3"] != ''
          if syllable_count(r.params["verse3"], 5)
            @haiku = Haiku[r.session["haiku_id"]]
            @haiku.update(verse3: r.params["verse3"]) if @haiku
            r.redirect "/genie/4"
          else
            flash[:info] = HAIKU_COUNT
            r.redirect "/genie/3"
          end
        else
          flash[:error] = "Please enter your third verse to continue."
          r.redirect "/genie/3"
        end
      end
      
      r.get "4" do
        @haiku = Haiku[session["haiku_id"]] 
        view("genie4") 
      end
    end
```

This would total 4 branches, 3 of which branch out into GET and POST. For now, the created haiku is just returned on page 4. Offering to add it to the anthology, proposing to associate a name or pseudonym with it for the record, then giving access to the content of the anthology will add more branches to this "Genie" (for "gen NI", or generative natural intelligence) branch of our Roda tree. That would be another day's work.


[python-nini]: https://anbarto.pythonanywhere.com