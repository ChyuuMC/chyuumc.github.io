---
layout: archives
# multilingual page pair id, this must pair with translations of this page. (This name must be unique)
lng_pair: id_archives

# publish date (used for seo)
# if not specified, site.time will be used.
#date: 2022-03-03 12:32:00 +0000

# for override items in _data/lang/[language].yml
#title: My title
#button_name: "My button"
# for override side_and_top_nav_buttons in _data/conf/main.yml
#icon: "fa fa-bath"

# seo
# if not specified, date will be used.
#meta_modify_date: 2022-03-03 12:32:00 +0000
# check the meta_common_description in _data/owner/[language].yml
#meta_description: ""

# optional
# if you enabled image_viewer_posts you don't need to enable this. This is only if image_viewer_posts = false
#image_viewer_on: true
# if you enabled image_lazy_loader_posts you don't need to enable this. This is only if image_lazy_loader_posts = false
#image_lazy_loader_on: true
# exclude from on site search
#on_site_search_exclude: true
# exclude from search engines
#search_engine_exclude: true
# to disable this page, simply set published: false or delete this file
#published: false
---

{%- include multi_lng/get-pages-by-lng.liquid pages = site.posts -%}
{%- assign postsByYear = lng_pages | sort: 'date' | reverse | group_by_exp:"post", "post.date | date: site.data.lang[lng].date.year" -%}

<script>
    function convert_month(p1) {
        en_months = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'];
        my_months = ['ဇန်နဝါရီလ', 'ဖေဖော်ဝါရီလ', 'မတ်လ', 'ဧပြီလ', 'မေလ', 'ဇွန်လ', 'ဂျူလိုင်လ', 'ဩဂုတ်လ', 'စက်တင်ဘာလ', 'အောက်တိုဘာလ', 'နိုဝင်ဘာလ', 'ဒီဇင်ဘာလ'];
        for (let i = 0; i < 12; i++) {
            if (!p1.localeCompare(en_months[i])) {
                return my_months[i];
            }
        }
    }
</script>

<div class="multipurpose-container">
  <h1>{{ site.data.lang[lng].archives.page_header }}</h1>
  <div class="archives">
    {%- for year in postsByYear %}
    <div class="year">
      <h6>{{ year.name }}</h6>
      {%- comment %}we can directly filter days. But I wanted to leave in case list by month needs{% endcomment -%}
      {%- assign postsByMonth = year.items | sort: 'date' | reverse | group_by_exp:"post", "post.date | date: '%m'" -%}
      {%- for month in postsByMonth -%}
      <div class="month">
        {%- comment %}convert string to integer{% endcomment -%}
        {%- assign monthInt = month.name | plus: 0 -%}
        {%- comment %}-1, since array starts from zero index{% endcomment -%}
        {%- assign monthInt = monthInt | minus: 1 %}
        <h6><script>document.write(convert_month('{{ site.data.lang[lng].date.months[monthInt] }}'))</script></h6>
        <ul>
        {%- for post in month.items %}
          <li>
            <span>{{ post.date | date: site.data.lang[lng].date.day }}</span>
            {%- assign page_title = post.title -%}
            {%- include util/auto-content-post-title-rename.liquid title = page_title -%}
            <a href="{{ post.url | relative_url }}">{{ page_title }}</a>
          </li>
        {%- endfor %}
        </ul>
      </div>
      {% endfor -%}
    </div>
    {%- endfor %}
  </div>
</div>
