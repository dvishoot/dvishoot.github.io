+++
title = '{{ replace .File.ContentBaseName "-" " " | title }}'
date = '{{ .Date }}'
draft = true
tags = []
series = []
categories = [
{{- if in .File.Dir "posts/engineering" -}}
  "engineering",
{{- else if in .File.Dir "posts/adventures" -}}
  "adventures",
{{- end -}}
]

[params]
pillar = '{{- if in .File.Dir "posts/engineering" -}}engineering{{- else if in .File.Dir "posts/adventures" -}}adventures{{- else -}}{{- end -}}'
+++

## Context

## Notes
