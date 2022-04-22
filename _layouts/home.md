---
# Mr. Green Jekyll Theme - v1.0.1 (https://github.com/MrGreensWorkshop/MrGreen-JekyllTheme)
# Copyright (c) 2022 Mr. Green's Workshop https://www.MrGreensWorkshop.com
# Licensed under MIT

layout: default
# main page (index.html)
---

{%- include multi_lng/get-pages-by-lng.liquid pages = site.posts -%}

<div class="multipurpose-container home-heading-container">
  <div class="home-heading" style="background-image:url('{{ page.img }}');">
    <div class="home-heading-message">
      {{ site.data.lang[lng].home.top_header_line1 | replace: site.data.conf.main.brand_replace, site.data.owner.brand }}
      {%- if site.data.lang[lng].home.top_header_line2 %}
        <br>
        {{ site.data.lang[lng].home.top_header_line2 | replace: site.data.conf.main.brand_replace, site.data.owner.brand }}
      {% endif -%}
    </div>
  </div>
  <div class="home-intro-text">
    <h1>Summary</h1>
    저는 Front-end의 코드의 변화를 직접적으로 볼 수 있는 매력에 빠져있는 정혜연입니다.
    <br />
    <ul>
      <li> 컴퓨터공학과 19학번 </li>
      <li> 팀스피노 Front-end 담당 </li>
      <li> TILON intern 직무 </li>
      <li> Niagara College 해외 연수 </li>
    </ul>
    <br />
    <h2>Github 저장소</h2>
    <a href="https://github.com/HY219">https://github.com/HY219 </a>
    <br />
    <h2>fork Repositories</h2>
    <ul>
      <li> react-native</li>
        <br />
        <blockquote>이번 2022년 캡스톤 디자인에서 react-native로 app개발을 진행하면서, 공부를 하다 보니깐 관심이 생겼습니다.
          react-native는 cross paltform을 지원하기 때문에 IOS와 Android를 동시에 개발 할 수 있는 장점이 있습니다
        </blockquote>
      <li> redux </li>
          <br />
        <blockquote>Front-end에서 가장 중요한 state 관리를 유용하게 해줍니다, react 같은 경우 state를 하향식으로 관리를 하기 때문에 반대로 state를 전달하기 어렵습니다, 하지만 redux를 사용하면 전역 state를 쉽게 관리 할 수 있는 장점이 있습ㄴ디ㅏ
        </blockquote>
      <li> VTK.js </li>
          <br />
      <blockquote> 3D 모델링을 웹에서도 가능하게 해주는 라이브러리입니다. 최근에 3D 모델링에 관심이 생겼는데, 제가 할수있는 언어인 JS로 가능하다는 점이 매력적으로 느껴져서 공부중입니다.
        </blockquote>
    </ul>

  </div>
</div>

{%- if lng_pages.size > 0 and site.data.conf.others.home.new_posts %}

<div class="multipurpose-container new-posts-container">
  <h1>{{ site.data.lang[lng].home.new_posts_title }}</h1>
  <ul class="new-posts">
  {%- for _post in lng_pages limit: site.data.conf.others.home.new_posts_count_limit -%}
    <li>
      {%- assign page_title = _post.title -%}
      {%- include util/auto-content-post-title-rename.liquid title = page_title -%}
      <a href="{{ site.baseurl }}{{ _post.url }}">{{ page_title }}
        <span>{{ _post.date | date_to_string | date: site.data.lang[lng].date.long }}</span>
      </a>
    </li>
  {% endfor -%}
    <li>
      {%- include multi_lng/get-page-by-layout.liquid layout = 'archives' -%}
      <a href="{{ site.baseurl }}{{ layout_page_obj.url }}">{{ site.data.lang[lng].home.new_posts_show_more_button }}</a>
    </li>
  </ul>
</div>
{% endif -%}
