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

<div id="home" class="page-section" markdown="1">
  {% include_relative includes/intro.md %}
</div>

<div id="publications" class="page-section" markdown="1">
  {% include_relative includes/pub.md %}
</div>

<div id="educations" class="page-section" markdown="1">
  {% include_relative includes/educations.md %}
</div>

<div id="talks" class="page-section" markdown="1">
  {% include_relative includes/talks.md %}
</div>

<script>
document.addEventListener("DOMContentLoaded", function() {
    // 1. 获取所有的内容板块和导航链接
    const sections = document.querySelectorAll('.page-section');
    const navLinks = document.querySelectorAll('.greedy-nav a'); // 模板的导航链接class

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
        if (!sectionFound) {
            document.getElementById('home').style.display = 'block';
        }
    }

    // 3. 页面加载时，根据URL的锚点决定显示哪个板块
    const currentHash = window.location.hash.substring(1); // 获取URL中的锚点, 去掉'#'
    if (currentHash) {
        showSection(currentHash);
    } else {
        showSection('home'); // 如果没有锚点，默认显示 home 板块
    }

    // 4.为每一个导航链接添加点击事件
    navLinks.forEach(link => {
        link.addEventListener('click', function(e) {
            // 获取目标板块的ID (从 href="/#publications" 中提取 "publications")
            const targetId = this.getAttribute('href').split('#')[1];

            if (targetId) {
                // 阻止默认的滚动行为
                e.preventDefault();
                // 显示目标板块
                showSection(targetId);
                // 更新URL的锚点，这样用户可以复制和分享链接
                window.history.pushState(null, '', '#' + targetId);
            }
        });
    });

    // 5. 监听浏览器前进/后退按钮
    window.addEventListener('popstate', function() {
        const currentHash = window.location.hash.substring(1);
        if (currentHash) {
            showSection(currentHash);
        } else {
            showSection('home');
        }
    });
});
</script>