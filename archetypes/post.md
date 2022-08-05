+++
title = "{{ replace .Name "-" " " | title }}"
author = 'Patrick Lloyd'
date = {{ .Date }}
draft = true
tags = []
categories = []
series = []
searchHidden = false
[cover]
    image = "<image path/url>"
    # can also paste direct link from external site
    # ex. https://i.ibb.co/K0HVPBd/paper-mod-profilemode.png
    alt = "<alt text>"
    caption = "<text>"
    relative = false # To use relative path for cover image, used in hugo Page-bundles
ShowToc = true
ShowBreadCrumbs = true
+++

[//]: # "This archetype is for blog posts, either standalone or in a series."
[//]: # "The series variable is derived from the parent directory"

