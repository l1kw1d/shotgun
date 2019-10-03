FROM ubuntu:18.04

RUN \
	apt-get update -qq && \
	apt-get install -y -qqq \
		libck-dev \
		libluajit-5.1-dev \
		libpcap-dev \
		liblmdb-dev \
		libgnutls28-dev \
		luajit \
		libuv1-dev \
		libgoogle-perftools-dev \
		automake \
		libtool \
		pkg-config \
		git && \
	rm -rf /var/lib/apt/lists/*

RUN \
	git clone https://github.com/tomaskrizek/dnsjit.git && \
	cd dnsjit && \
	git checkout simulator && \
	./autogen.sh && \
	./configure && \
	make && \
	cd ..

RUN \
	git clone https://gitlab.labs.nic.cz/knot/shotgun.git && \
	cd shotgun && \
	cd ..

ENTRYPOINT ["dnsjit/src/dnsjit", "shotgun/shotgun.lua"]