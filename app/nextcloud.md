---
description: NextCloud
---

# NextCloud

## 安装部署

采用docker部署

#### docker-compose配置

```yaml
// Some code
version: "3.0"
services:
  nextcloud:
    image: nextcloud:latest
    container_name: nextcloud
    restart: always
    environment:
      PHP_MEMORY_LIMIT: 1G
    ports:
      - 80:80
    volumes:
      - /data/nextcloud:/var/www/html
```

## 视频缩略图

#### 安装ffmpeg

> docker exec -it --user root nextcloud sed -i 's/deb.debian.org/mirrors.ustc.edu.cn/g' /etc/apt/sources.list
>
> docker exec -it --user root nextcloud apt-get update
>
> docker exec -it --user root nextcloud apt-get -y install ffmpeg

#### 开启配置

> docker exec --user www-data nextcloud php occ config:system:set enable\_previews --value="true" --type=boolean
>
> docker exec --user www-data nextcloud php occ config:system:set enabledPreviewProviders 0 --value="OC\Preview\Movie"
>
> docker exec --user www-data nextcloud php occ config:system:set enabledPreviewProviders 1 --value="OC\Preview\HEIC"
>
> docker exec --user www-data nextcloud php occ config:system:set enabledPreviewProviders 2 --value="OC\Preview\MarkDown"
