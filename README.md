Adapted from [Charlie Park](http://charliepark.org/tags-in-jekyll/)
=======================

Overview
--------

Plugins included in this repository:

* **tag\_gen.rb** - Generates an index file for each tag listing the applicable posts for each
* **category\_gen.rb** - Generates an index file for each category listing the applicable posts for each

Usage
-----
Or for categories:

                category: automobiles



### tag\_gen.rb

Add tags in a post like this:

                tags:
                - jekyll
                - code

Create a layout generator:

                _layouts/tag_index.html

Put this code in the layout file:

                ---
                layout: default
                ---
                <h2 class="post_title">{.{page.title}}</h2>
                <ul>
                  {.% for post in site.posts %}
                  {.% for tag in post.tags %}
                  {.% if tag == page.tag %}
                  <li class="archive_list">
                    <time style="color:#666;font-size:11px;" datetime='{.{post.date | date: "%Y-%m-%d"}}'>{.{post.date | date: "%m/%d/%y"}}</time> <a class="archive_list_article_link" href='{.{post.url}}'>{.{post.title}}</a>
                    <p class="summary">{.{post.summary}}
                    <ul class="tag_list">
                      {.% for tag in post.tags %}
                      <li class="inline archive_list"><a class="tag_list_link" href="/tag/{.{ tag }}">{.{ tag }}</a></li>
                      {.% endfor %}
                    </ul>
                  </li>
                  {.% endif %}
                  {.% endfor %}
                  {.% endfor %}
                </ul>

Add this plugin as a submodule to your git repo:

                git submodule add 

### category\_gen.rb

