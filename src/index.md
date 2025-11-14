---
layout: default
---

# Welcome to Anantone's Corner

This is currently a test website, with the [potential](https://anantone.me/projects/ruby-tools/2025/11/13/learning-bridgetown/) to become a blog
about programming and writing.

## Previous posts

<ul>
  <% collections.posts.each do |post| %>
    <li>
      <a href="<%= post.relative_url %>"><%= post.data.title %> (#<%= post.data.categories[0] %>)</a>
    </li>
  <% end %>
</ul>



----

