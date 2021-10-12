+++
title = "{{ .Name }}"
author = "Cameron Farmer"
workingDirectory = "{{ if eq .File.BaseFileName "_index"}}~/root/{{.File.Dir}}{{else}}~/root/{{.File.Path}}{{end}}"
weight = 0 [comment]: (Weight pertains to the precedence pages take, with 1 being the highest precedence. 0 is considered un-set precedence level)
+++

