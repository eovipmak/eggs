FROM 		--platform=$TARGETOS/$TARGETARCH debian:bullseye-slim

LABEL       org.opencontainers.image.source="https://github.com/eovipmak/eggs"
LABEL       org.opencontainers.image.licenses=MIT

ENV         DEBIAN_FRONTEND=noninteractive

RUN			dpkg --add-architecture i386 \
			&& apt update \
			&& apt upgrade -y \
			&& apt install -y lib32gcc-s1 lib32stdc++6 unzip curl iproute2 tzdata libgdiplus libsdl2-2.0-0:i386 \
			&& curl -sL https://deb.nodesource.com/setup_18.x | bash - \
			&& apt install -y nodejs \
			&& npm install -g ws \
			&& useradd -d /home/container -m container

USER 		container
ENV  		USER=container HOME=/home/container

WORKDIR 	/home/container

COPY 		./entrypoint.sh /entrypoint.sh
COPY 		./wrapper.js /wrapper.js

CMD			[ "/bin/bash", "/entrypoint.sh" ]
