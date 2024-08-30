FFmpeg README
=============

ffmpeg modified version supports gapless aac.

## Compile

apt install build-essential nasm

apt install libmp3lame-dev libgnutls28-dev libvorbis-dev libfdk-aac-dev libopus-dev

./configure --prefix=/opt/ffmpeg-aac \
--extra-ldexeflags="-Wl,--rpath=/opt/ffmpeg-aac/lib" \
--enable-shared \
--disable-static \
--enable-pic \
--enable-gpl \
--enable-nonfree \
--enable-gnutls \
--enable-libfdk-aac \
--enable-libmp3lame \
--enable-libopus \
--enable-libvorbis \
--disable-librav1e \
--disable-sndio \
--disable-libmfx \
--disable-htmlpages

make -j $(nproc)

make install

## Run

/opt/ffmpeg-aac/bin/ffmpeg -i input.wav -hide_banner -y -c:a aac -nodelay_mode 1 output.aac

/opt/ffmpeg-aac/bin/ffmpeg -i input.wav -hide_banner -y -c:a libfdk_aac -nodelay_mode 1 output.aac


## License

FFmpeg codebase is mainly LGPL-licensed with optional components licensed under
GPL. Please refer to the LICENSE file for detailed information.
