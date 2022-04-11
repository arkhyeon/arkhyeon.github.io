---
layout: single
title: "Gitlog Config"
excerpt: "글작성 / 카테고리"

categories:
  - ETC
tags:
  - [blog]

toc: trues
toc_sticky: true
 
date: 2022-04-11
last_modified_at: 2022-04-11
---

# 글 작성

```md
폴더 : arkhyeon.github.io/_posts/
---
layout: single
title: "제목"
excerpt: "설명글"

categories:
  - 카테고리
tags:
  - [태그, 들]

toc: trues
toc_sticky: true
 
date: 작성날짜2022-04-02
last_modified_at: 마지막 수정일2022-04-02
---
본문 작성
```

# 카테고리
```html
폴더 : arkhyeon.github.io/_includes/nav_list_main
<li>
        <!--span 태그로 카테고리들을 크게 분류 ex) C/C++/C#-->
        <span class="nav__sub-title">SpringBoot</span>
        <!--ul 태그로 같은 카테고리들 모아둔 페이지들 나열-->
        <ul>
            <!--Cpp 카테고리 글들을 모아둔 페이지인 /categories/cpp 주소의 글로 링크 연결-->
            <!--category[1].size 로 해당 카테고리를 가진 글의 개수 표시--> 
            {% for category in site.categories %}
                {% if category[0] == "SpringBoot" %}
                    <li><a href="/categories/springboot" class="">SpringBoot ({{category[1].size}})</a></li>
                {% endif %}
            {% endfor %}
        </ul>
        <!--span 태그로 카테고리들을 크게 분류 ex) C/C++/C#-->
        <span class="nav__sub-title">React</span>
        <!--ul 태그로 같은 카테고리들 모아둔 페이지들 나열-->
        <ul>
            <!--Cpp 카테고리 글들을 모아둔 페이지인 /categories/cpp 주소의 글로 링크 연결-->
            <!--category[1].size 로 해당 카테고리를 가진 글의 개수 표시--> 
            {% for category in site.categories %}
                {% if category[0] == "React" %}
                    <li><a href="/categories/react" class="">React ({{category[1].size}})</a></li>
                {% endif %}
            {% endfor %}
        </ul>
      </li>
```

# 카테고리 - 페이지 생성
```json
폴더 : arkhyeon.github.io/_pages/categories/

---
title: "SpringBoot"
layout: archive
permalink: "/categories/springboot"
author_profile: true
sidebar_main: true
---
"{% assign posts = site.categories.SpringBoot %}"
"{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}"
```
