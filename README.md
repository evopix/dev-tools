# dev-tools

dev-tools is a collections if local docker development tools that makes development of docker based apps easier.

```
$ task init
task: [tools:install-windows] winget install FiloSottile.mkcert
task: [tools:install-windows] winget install gerardog.gsudo
task: [tools:install-windows] winget install BurntSushi.ripgrep.MSVC
task: [docker:init-network] docker network create --driver bridge localhost-dev
bf37ccc5c70921ac205698bafa14adea5c479e904e0dfe4efdbd713fdce91691
task: [cert:init] mkcert -install
Created a new local CA 💥
The local CA is now installed in the system trust store! ⚡️
Note: Firefox support is not available on your platform. ℹ️

task: [cert:init] mkdir -p etc/traefik/certs
task: [cert:init] mkcert -cert-file etc/traefik/certs/dev-tools.pem --key-file etc/traefik/certs/dev-tools-key.pem "*.dev.localhost"

Created a new certificate valid for the following names 📜
 - "*.dev.localhost"
   Warning: many browsers don't support second-level wildcards like "*.localhost" ⚠️

Reminder: X.509 wildcards only go one level deep, so this won't match a.b.localhost ℹ️

The certificate is at "etc/traefik/certs/dev-tools.pem" and the key at "etc/traefik/certs/dev-tools-key.pem" ✅

It will expire on 5 December 2026 🗓

task: [add-hostname 'foo'] sudo sh -c 'echo "127.0.0.1   foo.dev.localhost     # Added by dev-tools" >> C:/Windows/System32/drivers/etc/hosts'

$ task up
task: [up] docker compose up -d
[+] Running 1/1
 ✔ Container traefik-traefik-1  Started 
```

## Installation

### macOS

```
brew install go-task
git clone https://github.com/evopix/dev-tools.git
task init
task up
```

### Windows

```
winget install Task.Task
git clone https://github.com/evopix/dev-tools.git
task init
task up
```