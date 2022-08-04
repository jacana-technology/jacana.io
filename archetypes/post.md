+++
title = "{{ replace .Name "-" " " | title }}"
date = {{ .Date }}
draft = true
tags = []
categories = []
series = "{{ index (last 1 (split (path.Clean .File.Dir) "/")) 0 }}"
+++

[//]: # "This archetype is for blog posts, either standalone or in a series."
[//]: # "The series variable is derived from the parent directory"

