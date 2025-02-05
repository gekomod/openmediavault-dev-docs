---
title: Dev Create Plugin Script
description: 
published: 1
date: 2025-02-05T13:53:13.879Z
tags: 
editor: markdown
dateCreated: 2025-02-05T08:37:51.193Z
---

# Readme
Plugin creation script with sample files

# Download

```sh
wget -O generate_plugin https://github.com/gekomod/openmediavault-dev-plugin-create/raw/refs/heads/main/dist/generate_plugin && chmod +x generate_plugin
```

# Usage

```bash
./generate_plugin create myplugins services --config example1:1 port:90 name:Text,
./generate_plugin changelog  # if you have github repo
./generate_plugin deb PLUGINNAME # Generate a debian file .deb
```