---
title: "{{ replace .Name "-" " " | title }}"
author: "zero"
date: {{ .Date }}
categories: []
tags: []
archives: ["{{ dateFormat "2006-01" .Date }}"]
draft: true
---

<!--more-->
