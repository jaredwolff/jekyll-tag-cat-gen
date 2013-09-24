Adapted from [Charlie Park](http://charliepark.org/tags-in-jekyll/)
=======================

Overview
--------

Plugins included in this repository:

* **tag\_gen.rb** - Generates an index file for each tag listing the applicable posts for each
* **category\_gen.rb** - Generates an index file for each category listing the applicable posts for each

Usage
-----

### For both generators:

Add this plugin as a submodule to your git repo:

                git submodule add git@github.com:jaredwolff/tag_cat_gen.git _plugins/tag_cat_gen

### tag\_gen.rb

Add tags in a post like this:

                tags:
                - jekyll
                - code

Create a layout generator:

                _layouts/tag_index.html

Put this code in the layout file:

                ---
                layout: blog
                ---
                <div class="content-window">
                  <h2 class="post-title">{{page.title}}</h2>
                  <ul class="unstyled">
                    {% for post in site.posts %}
                    {% for tag in post.tags %}
                    {% if tag == page.tag %}
                    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ site.url }}{{ post.url }}">{{ post.title }}</a></li>
                    {% endif %}
                    {% endfor %}
                    {% endfor %}
                  </ul>
                </div>

### category\_gen.rb

Add tags in a post like this:

                category: automobiles

Create a layout generator:

                _layouts/category_index.html

Put this code in the layout file:

                ---
                layout: blog
                ---
                <div class="content-window">
                  <h2 class="post-title">{{page.title}}</h2>
                  <ul class="unstyled">
                    {% for post in site.posts %}
                    {% for category in post.categories %}
                    {% if category == page.category %}
                    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ site.url }}{{ post.url }}">{{ post.title }}</a></li>
                    {% endif %}
                    {% endfor %}
                    {% endfor %}
                  </ul>
                </div>

###Final note:

Customize as to your needs.