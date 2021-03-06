FROM registry.access.redhat.com/ubi8-minimal

LABEL MAINTAINERS="Red Hat Services"

ARG asciidoctor_version=2.0.10
ARG asciidoctor_confluence_version=0.0.2
ARG asciidoctor_pdf_version=1.5.3
ARG asciidoctor_diagram_version=1.5.19
ARG asciidoctor_epub3_version=1.5.0.alpha.12
ARG asciidoctor_mathematical_version=0.3.1
ARG asciidoctor_revealjs_version=2.0.0
ARG kramdown_asciidoc_version=1.0.1


ENV ASCIIDOCTOR_VERSION=${asciidoctor_version} \
  ASCIIDOCTOR_CONFLUENCE_VERSION=${asciidoctor_confluence_version} \
  ASCIIDOCTOR_PDF_VERSION=${asciidoctor_pdf_version} \
  ASCIIDOCTOR_DIAGRAM_VERSION=${asciidoctor_diagram_version} \
  ASCIIDOCTOR_EPUB3_VERSION=${asciidoctor_epub3_version} \
  ASCIIDOCTOR_MATHEMATICAL_VERSION=${asciidoctor_mathematical_version} \
  ASCIIDOCTOR_REVEALJS_VERSION=${asciidoctor_revealjs_version} \
  KRAMDOWN_ASCIIDOC_VERSION=${kramdown_asciidoc_version}



USER root

RUN microdnf install tar gzip make cmake python3 python3-setuptools ruby-devel gcc redhat-rpm-config zlib-devel patch git gcc-c++ glib2-devel

# Installing Ruby Gems needed in the image
# including asciidoctor itself
# TODO: have to find Lasem dev libs     "asciidoctor-mathematical:${ASCIIDOCTOR_MATHEMATICAL_VERSION}" \
RUN gem install --no-document \
    "asciidoctor:${ASCIIDOCTOR_VERSION}" \
    "asciidoctor-confluence:${ASCIIDOCTOR_CONFLUENCE_VERSION}" \
    "asciidoctor-diagram:${ASCIIDOCTOR_DIAGRAM_VERSION}" \
    "asciidoctor-epub3:${ASCIIDOCTOR_EPUB3_VERSION}" \
    asciimath \
    "asciidoctor-pdf:${ASCIIDOCTOR_PDF_VERSION}" \
    "asciidoctor-revealjs:${ASCIIDOCTOR_REVEALJS_VERSION}" \
    coderay \
    epubcheck-ruby:4.2.2.0 \
    haml \
    kindlegen:3.0.5 \
    "kramdown-asciidoc:${KRAMDOWN_ASCIIDOC_VERSION}" \
    rouge \
    slim \
    thread_safe \
    tilt

# Installing Python dependencies for additional
# functionnalities as diagrams or syntax highligthing
RUN pip3 install \
    actdiag \
    'blockdiag[pdf]' \
    nwdiag \
    seqdiag

WORKDIR /documents
VOLUME /documents

USER 1001

CMD ["/bin/bash"]

