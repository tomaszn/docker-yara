![YARA-logo](https://raw.githubusercontent.com/tomaszn/docker-yara/master/logo.png)

# Yara Dockerfile

[![Docker Image](https://img.shields.io/badge/docker%20image-60MB-blue.svg)](https://ghcr.io/tomaszn/docker-yara)

This repository contains a **Dockerfile** of [Yara](https://virustotal.github.io/yara/), and automatically publishes built images.

---

## Image Tags

```bash
IMAGE                                    SIZE
ghcr.io/tomaszn/docker-yara:4            60MB
ghcr.io/tomaszn/docker-yara:4-w-rules    66MB
```

> **NOTE:**
>
> - tags **-rules** come with some default yara rules included in the /rules directory.

## Installation

1. Install [Docker](https://docs.docker.com).
2. Download an image, e.g.: `docker pull ghcr.io/tomaszn/docker-yara:4`

## Getting Started

```bash
$ docker run --rm -v /path/to/rules:/rules:ro \
                  -v /path/to/malware:/malware:ro \
                  ghcr.io/tomaszn/docker-yara:4 /rules/RULES_FILE FILE
```

```
YARA 3.6.0, the pattern matching swiss army knife.
Usage: yara [OPTION]... RULES_FILE FILE | DIR | PID

Mandatory arguments to long options are mandatory for short options too.

  -t,  --tag=TAG                   print only rules tagged as TAG
  -i,  --identifier=IDENTIFIER     print only rules named IDENTIFIER
  -n,  --negate                    print only not satisfied rules (negate)
  -D,  --print-module-data         print module data
  -g,  --print-tags                print tags
  -m,  --print-meta                print metadata
  -s,  --print-strings             print matching strings
  -L,  --print-string-length       print length of matched strings
  -e,  --print-namespace           print rules' namespace
  -p,  --threads=NUMBER            use the specified NUMBER of threads to scan a directory
  -l,  --max-rules=NUMBER          abort scanning after matching a NUMBER of rules
  -d VAR=VALUE                     define external variable
  -x MODULE=FILE                   pass FILE's content as extra data to MODULE
  -a,  --timeout=SECONDS           abort scanning after the given number of SECONDS
  -k,  --stack-size=SLOTS          set maximum stack size (default=16384)
  -r,  --recursive                 recursively search directories
  -f,  --fast-scan                 fast matching mode
  -w,  --no-warnings               disable warnings
       --fail-on-warnings          fail on warnings
  -v,  --version                   show version information
  -h,  --help                      show this help and exit

Send bug reports and suggestions to: vmalvarez@virustotal.com.
```

Add the following to your bash or zsh profile

```bash
alias yara='docker run -it --rm -v $(pwd):/malware:ro ghcr.io/tomaszn/docker-yara:4 $@'
```

## Documentation

### Usage

```bash
$ yara [OPTION]... RULES_FILE FILE | DIR | PID
```

## Issues

Find a bug? Want more features? Find something missing in the documentation? Let me know! Please don't hesitate to [file an issue](https://github.com/tomaszn/docker-yara/issues/new).

## License

MIT Copyright (c) 2014 **blacktop**
