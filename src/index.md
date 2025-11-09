---
layout: default
---

# Welcome to Anantone's Corner

This is currently a test website, with the potential to become a kind of blog
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

