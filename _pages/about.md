---
permalink: /
title: ""
excerpt: ""
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

{% if site.google_scholar_stats_use_cdn %}
{% assign gsDataBaseUrl = "https://cdn.jsdelivr.net/gh/" | append: site.repository | append: "@" %}
{% else %}
{% assign gsDataBaseUrl = "https://raw.githubusercontent.com/" | append: site.repository | append: "/" %}
{% endif %}
{% assign url = gsDataBaseUrl | append: "google-scholar-stats/gs_data_shieldsio.json" %}

<div id="home" class="page-section">
  {% capture intro_content %}{% include_relative includes/intro.md %}{% endcapture %}
  {{ intro_content | markdownify }}
</div>

<div id="publications" class="page-section">
  {% capture pub_content %}{% include_relative includes/pub.md %}{% endcapture %}
  {{ pub_content | markdownify }}
</div>

<div id="educations" class="page-section">
  {% capture edu_content %}{% include_relative includes/educations.md %}{% endcapture %}
  {{ edu_content | markdownify }}
</div>

<div id="talks" class="page-section">
  {% capture talks_content %}{% include_relative includes/talks.md %}{% endcapture %}
  {{ talks_content | markdownify }}
</div>

{% assign my_articles = site.pages | where_exp: "item", "item.path contains '_pages/posts/'" %}
{% for article in my_articles %}
  <div id="{{ article.slug }}" class="page-section" style="display: none;">
    <h1>{{ article.title }}</h1>
    <hr>
    {{ article.content }}
  </div>
{% endfor %}

<script>
document.addEventListener("DOMContentLoaded", function() {
    // 1. 获取所有的内容板块
    const sections = document.querySelectorAll('.page-section');

    // 2. 定义一个函数，用来显示指定的板块，隐藏其他所有板块
    function showSection(targetId) {
        let sectionFound = false;
        sections.forEach(section => {
            if (section.id === targetId) {
                section.style.display = 'block';
                sectionFound = true;
            } else {
                section.style.display = 'none';
            }
        });
        // 如果找不到匹配的板块 (例如点击了主页链接)，就显示 home 板块
        if (!sectionFound && document.getElementById('home')) {
            document.getElementById('home').style.display = 'block';
        }
    }

    // 3. 页面加载时，根据URL的锚点决定显示哪个板块
    const currentHash = window.location.hash.substring(1);
    if (currentHash) {
        showSection(currentHash);
    } else {
        showSection('home'); // 如果没有锚点，默认显示 home 板块
    }

    // 4. 为页面上所有内部锚点链接添加点击事件 (已修正)
    const allAnchorLinks = document.querySelectorAll('a[href*="#"]');

    allAnchorLinks.forEach(link => {
        link.addEventListener('click', function(e) {
            const href = this.getAttribute('href');
            // 确保链接不是简单的 "#"
            if (href.length > 1) {
                const targetId = href.split('#')[1];

                if (targetId) {
                    // 阻止默认的滚动行为
                    e.preventDefault();
                    // 显示目标板块
                    showSection(targetId);
                    // 更新URL的锚点，这样用户可以复制和分享链接
                    window.history.pushState(null, null, '#' + targetId);
                }
            }
        });
    });

    // 5. 监听浏览器前进/后退按钮
    window.addEventListener('popstate', function() {
        const currentHashOnPop = window.location.hash.substring(1);
        if (currentHashOnPop) {
            showSection(currentHashOnPop);
        } else {
            showSection('home');
        }
    });
});
</script>