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
$ docker run --rm -v "$PWD"/rules:/rules:ro -v "$PWD"/malware:/malware:ro ghcr.io/tomaszn/docker-yara:4 /rules/RULES_FILE SAMPLE_FILE
```

`SAMPLE_FILE` can be a HTTP/HTTPS URL, in that case it will be downloaded.

If `SAMPLE_FILE` is a Zip file or a Chrome extension, it will be unarchived before scanning. If `ARCHIVE_DIR_SUFFIX` environment variable is provided, then it will be used in `mktemp -d --suffix=...`, so Yara output will contain this string in the path of the file (useful if many files are scanned).

```
YARA 4.0.5, the pattern matching swiss army knife.
Usage: yara [OPTION]... [NAMESPACE:]RULES_FILE... FILE | DIR | PID

Mandatory arguments to long options are mandatory for short options too.

       --atom-quality-table=FILE        path to a file with the atom quality table
  -C,  --compiled-rules                 load compiled rules
  -c,  --count                          print only number of matches
  -d,  --define=VAR=VALUE               define external variable
       --fail-on-warnings               fail on warnings
  -f,  --fast-scan                      fast matching mode
  -h,  --help                           show this help and exit
  -i,  --identifier=IDENTIFIER          print only rules named IDENTIFIER
  -l,  --max-rules=NUMBER               abort scanning after matching a NUMBER of rules
       --max-strings-per-rule=NUMBER    set maximum number of strings per rule (default=10000)
  -x,  --module-data=MODULE=FILE        pass FILE's content as extra data to MODULE
  -n,  --negate                         print only not satisfied rules (negate)
  -w,  --no-warnings                    disable warnings
  -m,  --print-meta                     print metadata
  -D,  --print-module-data              print module data
  -e,  --print-namespace                print rules' namespace
  -S,  --print-stats                    print rules' statistics
  -s,  --print-strings                  print matching strings
  -L,  --print-string-length            print length of matched strings
  -g,  --print-tags                     print tags
  -r,  --recursive                      recursively search directories (follows symlinks)
       --scan-list                      scan files listed in FILE, one per line
  -k,  --stack-size=SLOTS               set maximum stack size (default=16384)
  -t,  --tag=TAG                        print only rules tagged as TAG
  -p,  --threads=NUMBER                 use the specified NUMBER of threads to scan a directory
  -a,  --timeout=SECONDS                abort scanning after the given number of SECONDS
  -v,  --version                        show version information

Send bug reports and suggestions to: vmalvarez@virustotal.com.
```

Add the following to your bash or zsh profile to simply run "yara" command:

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

MIT Copyright (c) 2014 **blacktop**, modified by (c) 2021 **tomaszn**
