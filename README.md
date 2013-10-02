# `classic` -  Pluto Template Pack - Planet Planet Classic Style

## What's Pluto?

Pluto is a feed reader that lets you build web pages from published
web feeds. More [Pluto Project Site »](https://github.com/feedreader/pluto)

## What's Planet Planet?

Planet Planet is the very first planet feed reader coded in Python
by Scott James Remnant and Jeff Waugh [(Site)](http://www.planetplanet.org) - uses
Mark Pilgrim's universal feed parser (RDF, RSS and Atom)
and Tomas Styblo's templating engine; last release version 2.0 in 2006.


## Template Cheatsheet - Planet Planet | Pluto

    <TMPL_VAR name>                |  <%= site.name %>  or  <%= site.title %>
    <TMPL_VAR generator>           |  <%= Pluto.generator %>
    
    <TMPL_LOOP Channels>           |  <% site.feeds do |feed| %>
       <TMPL_VAR link>             |    <%= feed.link %>  or  <%= feed.url %>
       <TMPL_VAR name>             |    <%= feed.name %>  or  <%= feed.title %>
       <TMPL_VAR title>            |    <%= feed.title2 %>
       <TMPL_VAR url>              |    <%= feed.feed %>  or  <%= feed.feed_url %>
    </TMPL_LOOP>                   |  <% end %>
    
    <TMPL_LOOP Items>              |  <% items = site.items.latest.limit(24)
                                   |     ItemCursor.new( items ).each do |item,new_date,new_feed| %>
                                   |
      <TMPL_IF new_date>           |    <% if new_date %>
        <TMPL_VAR new_date>        |      <%= item.published_at %>
      </TMPL_IF>                   |    <% end %>
                                   |
      <TMPL_IF new_channel>        |    <% if new_feed %>
        <TMPL_VAR channel_link>    |      <%= item.feed.link %> or <%= item.feed.url %>
        <TMPL_VAR channel_name>    |      <%= item.feed.name %> or <%= item.feed.title %>
        <TMPL_VAR channel_title>   |      <%= item.feed.title2 %>
      </TMPL_IF>                   |    <% end %>
                                   |
      <TMPL_IF title>              |    <% if item.title %>
        <TMPL_VAR link>            |      <%= item.link %> or <% item.url %>
        <TMPL_VAR title>           |      <%= item.title %>
      </TMPL_IF>                   |    <% end %>
                                   |
      <TMPL_VAR content>           |    <% item.content %>
      <TMPL_VAR link>              |    <% item.link %> or <% item.url %>
      <TMPL_VAR date>              |    <% item.published_at %>
                                   |
      <TMPL_IF author>             |
        <TMPL_VAR author>          |    to be done
      </TMPL_IF>                   |
    </TMPL_LOOP>                   |  <% end %>
    
    <TMPL_VAR date>                |  <%= site.fetched_at %>     # site (planet) last updated



## Questions? Comments?

Send them along to the [Planet Pluto and Friends Forum/Mailing List](http://groups.google.com/group/feedreader).
Thanks!
