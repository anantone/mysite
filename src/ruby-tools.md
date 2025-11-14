---
layout: post
title: "Useful Ruby Tools"
---

<ul>
  <% collections.posts.each do |post| %>
  <% if post.data.categories.include?('ruby-tools')%>
    <li>
      <a href="<%= post.relative_url %>"><%= post.data.title %></a>
    </li>
  <% end %>
  <% end %>
</ul>