FROM biocorecrg/debian-perlbrew:stretch

# File Author / Maintainer
MAINTAINER Toni Hermoso Pulido <toni.hermoso@crg.eu>
MAINTAINER Luca Cozzuto <lucacozzuto@gmail.com> 

ARG PYENV_ROOT=/usr/local/python
ARG PYTHON_VERSION=2.7.13

ENV PYENV_ROOT $PYENV_ROOT

RUN set -x; apt-get update; apt-get upgrade; apt-get install -y git libreadline-dev sqlite3 libsqlite3-dev libssl-dev zlib1g-dev libbz2-dev tk-dev

RUN bash -c 'curl -L https://raw.githubusercontent.com/pyenv/pyenv-installer/master/bin/pyenv-installer | bash'

ENV PATH $PYENV_ROOT/bin:$PATH
ENV PYTHON_VERSION $PYTHON_VERSION

RUN pyenv install $PYTHON_VERSION

ENV PATH="$PYENV_ROOT/shims:$PYENV_ROOT/versions/$PYTHON_VERSION/bin:$PATH"

RUN ln -s $PYENV_ROOT/versions/$PYTHON_VERSION/bin/python /usr/local/bin/python
RUN ln -s $PYENV_ROOT/versions/$PYTHON_VERSION/bin/python2 /usr/local/bin/python2
RUN ln -s $PYENV_ROOT/versions/$PYTHON_VERSION/bin/python2.7 /usr/local/bin/python2.7
RUN ln -s $PYENV_ROOT/versions/$PYTHON_VERSION/bin/pip /usr/local/bin/pip
RUN ln -s $PYENV_ROOT/versions/$PYTHON_VERSION/bin/pip2 /usr/local/bin/pip2
RUN ln -s $PYENV_ROOT/versions/$PYTHON_VERSION/bin/pip2.7 /usr/local/bin/pip2.7

# Clean cache
RUN apt-get clean
RUN set -x; rm -rf /var/lib/apt/lists/*


