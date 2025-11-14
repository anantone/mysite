---
layout: page
title: "Pet Projects"
---

<ul>
  <% collections.posts.each do |post| %>
  <% if post.data.categories.include?('projects')%>
    <li>
      <a href="<%= post.relative_url %>"><%= post.data.title %></a>
    </li>
  <% end %>
  <% end %>
</ul>