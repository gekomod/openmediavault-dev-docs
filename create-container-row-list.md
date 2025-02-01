---
title: Create Row Container List
description: 
published: 1
date: 2025-01-26T10:31:49.039Z
tags: 
editor: markdown
dateCreated: 2025-01-26T10:31:47.110Z
---

# Create Row Container List - File Structure

```tree
└──ContainerName
   ├──ContainerName.env
   ├──ContainerName.yml
   ├──Containername - This is icon
   └──readme
```

# ContainerName.env

   ```env
      Various Options
   ```

# ContainerName.yml

Example based on the radarr.yml file

  ```yml
  ---
services:
  radarr:
    image: lscr.io/linuxserver/radarr:latest
    container_name: radarr
    environment:
      - PUID=1000
      - PGID=100
      - TZ=Europe/Istanbul
    volumes:
      - CHANGE_TO_COMPOSE_DATA_PATH/radarr/config:/config
      - CHANGE_TO_COMPOSE_DATA_PATH/radarr/movies:/movies
      - CHANGE_TO_COMPOSE_DATA_PATH/radarr/downloads:/downloads
    ports:
      - 7878:7878
    restart: unless-stopped
  ```

# Readme

```readme
Container description
```

# Icon

The icon should be downloaded to the container directory, i.e.

ContainerName/ContainerName

The icon must be without an ending, i.e. without .png .jpg .svg .bmp etc.