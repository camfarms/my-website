+++
title = "{{ .Name }}"
author = "Cameron Farmer"
date = "{{ .Date }}"
workingDirectory = "{{ if eq .File.BaseFileName "_index"}}~/root/{{.File.Dir}}{{else}}~/root/{{.File.Path}}{{end}}"
weight = 0 
draft = true
toc = false
description = "Placeholder_description"
+++

