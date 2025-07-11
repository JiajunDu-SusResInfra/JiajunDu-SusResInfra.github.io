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
<span class='anchor' id='about-me'></span>

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus ornare aliquet ipsum, ac tempus justo dapibus sit amet. Suspendisse condimentum, libero vel tempus mattis, risus risus vulputate libero, elementum fermentum mi neque vel nisl. Maecenas facilisis maximus dignissim. Curabitur mattis vulputate dui, tincidunt varius libero luctus eu. Mauris mauris nulla, scelerisque eget massa id, tincidunt congue felis. Sed convallis tempor ipsum rhoncus viverra. Pellentesque nulla orci, accumsan volutpat fringilla vitae, maximus sit amet tortor. Aliquam ultricies odio ut volutpat scelerisque. Donec nisl nisl, porttitor vitae pharetra quis, fringilla sed mi. Fusce pretium dolor ut aliquam consequat. Cras volutpat, tellus accumsan mattis molestie, nisl lacus tempus massa, nec malesuada tortor leo vel quam. Aliquam vel ex consectetur, vehicula leo nec, efficitur eros. Donec convallis non urna quis feugiat.

My research interest includes neural machine translation and computer vision. I have published more than 3 papers at the top international journal with total <a href='https://scholar.google.com/citations?user=R41lYV0AAAAJ'>google scholar citations <strong><span id='total_cit'>20+</span></strong></a> (You can also use google scholar badge <a href='https://scholar.google.com/citations?user=R41lYV0AAAAJ'><img src="https://img.shields.io/endpoint?url={{ url | url_encode }}&logo=Google%20Scholar&labelColor=f6f6f6&color=9cf&style=flat&label=citations"></a>).


# 🔥 News
- *2022.02*: &nbsp;🎉🎉 Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus ornare aliquet ipsum, ac tempus justo dapibus sit amet. 
- *2022.02*: &nbsp;🎉🎉 Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus ornare aliquet ipsum, ac tempus justo dapibus sit amet. 
</div>

<div id="publications" class="page-section" markdown="1">
# 📝 Publications 

<div class='paper-box'><div class='paper-box-image'><div><div class="badge">CVPR 2016</div><img src='images/500x300.png' alt="sym" width="100%"></div></div>
<div class='paper-box-text' markdown="1">

[Deep Residual Learning for Image Recognition](https://openaccess.thecvf.com/content_cvpr_2016/papers/He_Deep_Residual_Learning_CVPR_2016_paper.pdf)

**Kaiming He**, Xiangyu Zhang, Shaoqing Ren, Jian Sun

[**Project**](https://scholar.google.com/citations?view_op=view_citation&hl=zh-CN&user=DhtAFkwAAAAJ&citation_for_view=DhtAFkwAAAAJ:ALROH1vI_8AC) <strong><span class='show_paper_citations' data='DhtAFkwAAAAJ:ALROH1vI_8AC'></span></strong>
- Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus ornare aliquet ipsum, ac tempus justo dapibus sit amet. 
</div>
</div>

- [Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus ornare aliquet ipsum, ac tempus justo dapibus sit amet](https://github.com), A, B, C, **CVPR 2020**
</div>

<div id="honors" class="page-section" markdown="1">
# 🎖 Honors and Awards
- *2021.10* Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus ornare aliquet ipsum, ac tempus justo dapibus sit amet. 
- *2021.09* Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus ornare aliquet ipsum, ac tempus justo dapibus sit amet. 
</div>

<div id="educations" class="page-section" markdown="1">
# 📖 Educations
- *2019.06 - 2022.04 (now)*, Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus ornare aliquet ipsum, ac tempus justo dapibus sit amet. 
- *2015.09 - 2019.06*, Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus ornare aliquet ipsum, ac tempus justo dapibus sit amet. 
</div>

<div id="talks" class="page-section" markdown="1">
# 💬 Invited Talks
- *2021.06*, Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus ornare aliquet ipsum, ac tempus justo dapibus sit amet. 
- *2021.03*, Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus ornare aliquet ipsum, ac tempus justo dapibus sit amet.  \| [\[video\]](https://github.com/)
</div>

<div id="internships" class="page-section" markdown="1">
# 💻 Internships
- *2019.05 - 2020.02*, [Lorem](https://github.com/), China.
</div>

<script>
document.addEventListener("DOMContentLoaded", function() {
    // 1. 获取所有的内容板块和导航链接
    const sections = document.querySelectorAll('.page-section');
    const navLinks = document.querySelectorAll('.visible-links a'); // 模板的导航链接class

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