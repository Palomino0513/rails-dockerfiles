FROM postgres:11
MAINTAINER Jose Ivan Palominoi "palomino@agilgob.com"


# VARS
ENV RUBY_VERSION=2.4.1
ENV RAILS_VERSION=5.1.3
ENV USER=userRails


# Install dependences
RUN apt-get update
RUN apt-get install -y \
	build-essential \
	openssl \
	openssh-server \
	openssh-client \
	git-core \
	curl \
	wget \
	procps \
	net-tools \
	zlib1g \
	zlib1g-dev \
	# postgresql-client \
	# libreadline6 \
	libreadline6-dev \
	libssl-dev \
	libyaml-dev \
	libsqlite3-dev \
	sqlite3 \
	libxml2-dev \
	libxslt-dev \
	autoconf \
	libc6-dev \
	ncurses-dev \
	automake \
	libtool \
	bison \
	# subversion \
	pkg-config \
	libpq-dev



# Install RVM
RUN \curl -sSL https://github.com/rvm/rvm/tarball/stable -o rvm-stable.tar.gz
RUN echo 'export rvm_prefix="$HOME"' > /root/.rvmrc \
  && echo 'export rvm_path="$HOME/.rvm"' >> /root/.rvmrc \
  && mkdir rvm && cd rvm \
  && tar --strip-components=1 -xzf ../rvm-stable.tar.gz \
  && ./install --auto-dotfiles --autolibs=0 \
  && cd ../ && rm -rf rvm-stable stable.tar.gz rvm


# Install npm
RUN curl -sL https://deb.nodesource.com/setup_11.x | bash -
RUN apt-get install -y nodejs


# Post install RVM
RUN /bin/bash -c "source ~/.rvm/scripts/rvm"
RUN ~/.rvm/bin/rvm requirements



# Install ruby
RUN /bin/bash --login -c "rvm install $RUBY_VERSION"
RUN /bin/bash --login -c "rvm use $RUBY_VERSION --default"
RUN /bin/bash --login -c "rvm $RUBY_VERSION"


# config rvm
RUN /bin/bash --login -c "rvm gemset create default"
RUN /bin/bash --login -c "rvm $RUBY_VERSION@default"

# install rails
RUN /bin/bash --login -c "gem install rails -v $RAILS_VERSION"


WORKDIR /usr/src/app
