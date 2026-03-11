---
layout: page
permalink: /posts/
title: "Versions"
description: "Versions ..."
tags: [versions, history, builds, releases]
---

<div class="flex-center">
   <a href="{{ site.url }}/all/" class="button-view-full-archive open-sans-14-bold">List all changes</a>
</div>

<ul class="post-index unstyled-list">
{% for post in site.posts %}
  {% assign author = site.authors[post.author] %}
   <div class="post-item">
        <div class="history-icon"></div>
		<article itemscope itemtype="http://schema.org/Article">
			<div class="post-item-title">
                <a href="{{ site.url }}{{ post.url }}" itemprop="url">
                    {{ post.title }}
                </a>
			</div>
				<div class="entry-meta entry-meta-padding">
                    <span class="entry-date date published clusterTag"><time
                                datetime="{{ post.date | date_to_xmlschema }}"
                                itemprop="datePublished">{{ post.date | date: "%B %d, %Y" }}</time></span>
                    <div class="post-date">
                        <img class="gravatar" height="23"
                             src="https://2.gravatar.com/avatar/{{ author.gravatar }}?r=x&amp;s=140"
                             width="23">
                        <span class="author vcard" itemprop="author" itemscope
                              itemtype="http://schema.org/Person">
                            <span itemprop="name" class="fn">{{ author.name }}</span>
                        </span>
                    </div>
                </div>
			<div itemprop="description" class="issues-list">
  				{{ post.content | split:"<!--more-->" | first }}
            </div>
            {% assign postSecondPartSize = post.content | split:"<!--more-->" | slice:1 |  size %}
  			{% if postSecondPartSize > 0 %}
                <a class="show-all-changes" href="{{ site.url }}{{ post.url }}">
					<span>show all changes in this release</span>
				</a>
  			{% endif %}		                                       
		</article>
	</div>
{% endfor %}
</ul>
