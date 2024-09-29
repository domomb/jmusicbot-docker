# JMusicBot Docker
[![Release](https://img.shields.io/github/release/jagrosh/MusicBot?color=g&style=for-the-badge)](https://github.com/jagrosh/MusicBot/releases/latest)
![Supports amd64 Architecture](https://img.shields.io/badge/amd64-yes-blueviolet.svg?style=for-the-badge)
![Supports arm64 Architecture](https://img.shields.io/badge/arm64-yes-blueviolet.svg?style=for-the-badge)

A simple Docker container for [JMusicBot](https://github.com/xPrinny/MusicBot). This fork of the project updated the yml until the official source gets updated. The container will start up, then download JMusicBot from the projects repository and run it.

## Usage
- Place your **config.txt**, **Playlists** folder, and **serversettings.json** file (if you have one) in `/your/path/to/config`. This directory will be shared with the container.
  > Refer to the documentaion on how to [configure the bot](https://jmusicbot.com/setup/#3-configure-the-bot)
- You can specify a JMusicBot version using the environment variable `BOT_VERSION`. By default the latest version will be downloaded so you don't have to include the value if you want to use latest.
  > The version numbers you can use correspond to the [releases](https://github.com/jagrosh/MusicBot/releases)

### Docker examples
- Using docker cli
```bash
docker run -dit \  
  --name=jmusicbot \
  -v /your/path/to/config:/config \
  --restart=unless-stopped \
  ghcr.io/domomb/jmusicbot-docker
```

- Using docker compose
```bash
---
version: "3"
services:
  jmusicbot:
    image: ghcr.io/domomb/jmusicbot-docker
    container_name: jmusicbot
    volumes:
      - /your/path/to/config:/config
    restart: unless-stopped
```

---

#### Debugging
- If you need to access the container you can hop into it and get a shell using:
```bash
docker exec -it jmusicbot /bin/bash
```

- Or read the logs:
```bash
docker logs jmusicbot
```
