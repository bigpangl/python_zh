FROM bigpangl/python:3.6-alpine
#COPY ./ldd /pyinstaller/ldd
RUN apk --update --no-cache add \
        zlib-dev \
        musl-dev \
        libc-dev \
        libffi-dev \
        gcc \
        g++ \
    && pip download --no-deps pyinstaller==3.4  && tar zxvf PyInstaller-3.4.tar.gz -C /tmp  \
    && rm PyInstaller-3.4.tar.gz \
    && cd /tmp/PyInstaller-3.4/bootloader \
    && CFLAGS="-Wno-stringop-overflow" python ./waf configure --no-lsb all \
    && pip install .. \
    && chmod a+x /pyinstaller/* \
    && rm -Rf /tmp/PyInstaller-3.4 \
    && apk del zlib-dev \
        libffi-dev \
        libc-dev \
        g++
#ENV PATH /pyinstaller/:$PATH
