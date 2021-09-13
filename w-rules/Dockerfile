FROM ghcr.io/tomaszn/docker-yara:4

LABEL maintainer "https://github.com/tomaszn"

COPY rules /rules

VOLUME ["/malware"]
VOLUME ["/rules"]

WORKDIR /malware

# use this ENTRYPOINT to simply run YARA
#ENTRYPOINT ["yara"]

# use this ENTRYPOINT to unzip the sample if it is "application/zip"
ENTRYPOINT ["/maybe_unzip_to_tmp"]

CMD ["--help"]
