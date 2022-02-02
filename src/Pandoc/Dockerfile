FROM pandoc/latex:latest

RUN apk --no-cache add python3 py3-pip
RUN pip3 install pandoc-include

RUN mkdir $HOME/git
RUN mkdir $HOME/work

# run with e.g. docker run -v ${PWD}:/root/work --entrypoint /bin/sh -it container/tag.. 
# test locally
# /usr/local/bin/pandoc --from markdown --to pdf --filter pandoc-include Innholdsfortegnelse.md -o ../build/whitepaper2.pdf

ENTRYPOINT ["/usr/local/bin/pandoc"]