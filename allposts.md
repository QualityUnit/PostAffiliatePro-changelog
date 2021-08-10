---
layout: page
permalink: /all/
title: "All changes"
description: "Changes ..."
tags: [changelog, posts, all]
---

<ul class="post-index unstyled-list">
{% for post in site.posts %}
  {% assign author = site.authors[post.author] %}
   	<div class="post-item">
		<div class="history-icon"></div>
		<article itemscope itemtype="http://schema.org/Article">
			<div itemprop="url" style="margin:10px 0 30px;">
				<h2 itemprop="name">{{ post.title }}</h2>
				<div class="entry-meta entry-meta-padding">
					<i class="fa fa-calendar fa-fw"></i> <span class="entry-date date published clusterTag"><time datetime="{{ post.date | date_to_xmlschema }}" itemprop="datePublished" class="published{% unless page.modified %} updated{% endunless %}">{{ post.date | date: "%B %d, %Y" }}</time></span>
                    			<div class="post-date">
          					<img class="gravatar" height="23" src="https://2.gravatar.com/avatar/{{ author.gravatar }}?r=x&amp;s=140" width="23">
          					<span class="author vcard" itemprop="author" itemscope itemtype="http://schema.org/Person"><span itemprop="name" class="fn">{{ author.name }}</span></span>
					</div>
				</div>
				<div itemprop="description" class="issues-list">
          				{{ post.content }}
        			</div>
			</div>
		</article>
	</div>
{% endfor %}
</ul>
