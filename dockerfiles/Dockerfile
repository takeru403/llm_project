FROM python:3.10.12
USER root

#日本語のドキュメント
RUN apt-get update
RUN apt-get -y install locales && \
    localedef -f UTF-8 -i ja_JP ja_JP.UTF-8
ENV LANG ja_JP.UTF-8
ENV LANGUAGE ja_JP:ja
ENV LC_ALL ja_JP.UTF-8
ENV TZ JST-9
ENV TERM xterm
# pipのインストール
RUN curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py && \
    python get-pip.py
RUN mkdir -p /LLM_project/app
COPY . /LLM_project/app
WORKDIR /LLM_project/app
COPY dockerfiles/requirements.lock .
EXPOSE 8501

RUN apt-get install -y vim less
RUN pip install --upgrade pip
RUN pip install --upgrade setuptools
#あとでrequirements.lockに変更する。
RUN pip install -r /LLM_project/app/requirements.lockrequirements.lock
