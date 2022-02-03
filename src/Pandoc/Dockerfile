FROM pandoc/latex:latest

RUN apk --no-cache add python3 py3-pip
RUN pip3 install pandoc-include

RUN mkdir $HOME/git
RUN mkdir $HOME/work

RUN mkdir /github
RUN mkdir /github/workspace
# run with e.g. docker run -v ${PWD}:/github/workspace --entrypoint /bin/sh -it container/tag.. 

# /usr/local/bin/pandoc --from markdown --to pdf --filter pandoc-include Innholdsfortegnelse.md -o ../build/whitepaper2.pdf
# GH Actions runs under /github/workspace
# Do this from root git folder to test locally
# docker run -v ${PWD}:/github/workspace haraldf/pandoc-include --from markdown --to pdf --filter pandoc-include whitepaper/Innholdsfortegnelse.md -o build/whitepaper2.pdf
WORKDIR /github/workspace
ENTRYPOINT ["/usr/local/bin/pandoc"]