FROM pandoc/latex:latest

RUN apk --no-cache add python3 py3-pip
RUN pip3 install pandoc-include

ENTRYPOINT ["/usr/local/bin/pandoc"]