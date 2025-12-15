---
layout: page
title: "Documentation"
---
<ul>
  <% collections.posts.each do |post| %>
  <% if post.data.categories.include?('docs')%>
    <li>
      <a href="<%= post.relative_url %>"><%= post.data.title %></a>
    </li>
  <% end %>
  <% end %>
</ul>