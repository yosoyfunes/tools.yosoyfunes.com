# how to run container docker 

```bash
docker run --rm -ti -v $(pwd):/app -w /app php:8.0.7-cli-buster bash
```

```bash
Unable to find image 'php:8.0.7-cli-buster' locally
8.0.7-cli-buster: Pulling from library/php
69692152171a: Pull complete 
2040822db325: Pull complete 
9b4ca5ae9dfa: Pull complete 
ac1fe7c6d966: Pull complete 
7994240c01ee: Pull complete 
17d30fab02f4: Pull complete 
0e0d506afaf7: Pull complete 
dd2edbf3c029: Pull complete 
195ee400b641: Pull complete 
Digest: sha256:e1ee5a85f9c0f00258559ed806e113dc6f6721ff7d6e6ce35229ebe986aa84c6
Status: Downloaded newer image for php:8.0.7-cli-buster
```

```bash
php -v
```

```bash
PHP 8.0.7 (cli) (built: Jun  4 2021 18:34:28) ( NTS )
Copyright (c) The PHP Group
Zend Engine v4.0.7, Copyright (c) Zend Technologies
```
