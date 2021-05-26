FROM alpine:latest

# Enable additional apk repos
RUN echo 'https://dl-cdn.alpinelinux.org/alpine/edge/main' \
                       >> /etc/apk/repositories
RUN echo 'https://dl-cdn.alpinelinux.org/alpine/edge/community' \
                       >> /etc/apk/repositories

# Installing dependencies
RUN apk add -U mlocate \
                       poppler-utils \
                       poppler-dev \
                       libjpeg-turbo \
                       openjpeg \
                       libpng \
                       zlib \
                       freetype \
                       fontconfig \
                       nss \
                       lcms2 \
                       tiff \
                       expat \
                       jbig2enc \
                       jbig2dec \
                       jpeg-dev \
                       python3 \
                       python3-dev \
                       py3-pip \
                       py3-wheel \
                       alpine-sdk

RUN rm -rf pdf2image_layer;  mkdir -p pdf2image_layer/poppler_binaries;
RUN updatedb
RUN cp $(locate libpoppler.so) pdf2image_layer/poppler_binaries/.  # poppler-dev edge main
RUN cp $(which pdftoppm) pdf2image_layer/poppler_binaries/.  # poppler-utils edge main
RUN cp $(which pdfinfo) pdf2image_layer/poppler_binaries/.  # poppler-utils edge main
RUN cp $(which pdftocairo) pdf2image_layer/poppler_binaries/.  # poppler-utils edge main
RUN cp $(locate libjpeg.so.8 ) pdf2image_layer/poppler_binaries/.  # libjpeg-turbo edge main
RUN cp $(locate libopenjp2.so.7 ) pdf2image_layer/poppler_binaries/.  # openjpeg edge main
RUN cp $(locate libpng16.so.16 ) pdf2image_layer/poppler_binaries/.  # libpng edge main
RUN cp $(locate libz.so.1 ) pdf2image_layer/poppler_binaries/.  # zlib edge main
RUN cp $(locate libfreetype.so.6 ) pdf2image_layer/poppler_binaries/.  # freetype edge main
RUN cp $(locate libfontconfig.so.1 ) pdf2image_layer/poppler_binaries/.  # fontconfig edge main
RUN cp $(locate libnss3.so ) pdf2image_layer/poppler_binaries/.  # nss edge community
RUN cp $(locate libsmime3.so ) pdf2image_layer/poppler_binaries/.  # nss edge community
RUN cp $(locate liblcms2.so.2 ) pdf2image_layer/poppler_binaries/.  # lcms2 edge main
RUN cp $(locate libtiff.so.5 ) pdf2image_layer/poppler_binaries/.  # tiff edge main
RUN cp $(locate libexpat.so.1 ) pdf2image_layer/poppler_binaries/.  # expat edge main
# RUN cp $(locate libjbig.so.0 ) pdf2image_layer/poppler_binaries/.
RUN cp $(locate libjbig2enc.so.0) pdf2image_layer/poppler_binaries/.  # jbig2enc edge community
RUN cp $(locate libjbig2dec.so.0) pdf2image_layer/poppler_binaries/.  # jbig2enc edge community
RUN cp $(locate libfreetype.so.6) pdf2image_layer/poppler_binaries/.  # freetype edge main

# Install pdf2image
RUN python3 -m pip install --target python pdf2image
RUN cp -r python/ pdf2image_layer/
