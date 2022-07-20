---
layout: links
# multilingual page pair id, this must pair with translations of this page. (This name must be unique)
lng_pair: id_links

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


# you can always move this content to _data/content/ folder
# just create new file at _data/content/links/[language].yml and move content below.
###########################################################
#                Links Page Data
###########################################################
page_data:
  main:
    header: "Links"
    info: "Here you can find some useful links."

  # To change order of the Categories, simply change order. (you don't need to change list order.)
  category:
    - title: "Hradec Kralove"
      type: id_hradeckralove
      color: "green"
 #   - title: "Health"
 #     type: id_health
 #     color: "#F4A273"
 #   - title: "Adaptation"
 #     type: id_adaptation
 #     color: "#62b462"

  list:
      -
      # HradecKralove
      - type: id_hradeckralove
        title: "Aquacentrum Hradec Kralove"
        url: "http://www.snhk.cz/lazne"
        info: "Nice place to go in the summer (and winter)."
---