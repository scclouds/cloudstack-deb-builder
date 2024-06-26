# Licensed to the Apache Software Foundation (ASF) under one
# or more contributor license agreements.  See the NOTICE file
# distributed with this work for additional information
# regarding copyright ownership.  The ASF licenses this file
# to you under the Apache License, Version 2.0 (the
# "License"); you may not use this file except in compliance
# with the License.  You may obtain a copy of the License at
#
#   http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing,
# software distributed under the License is distributed on an
# "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
# KIND, either express or implied.  See the License for the
# specific language governing permissions and limitations
# under the License.

FROM ubuntu:20.04
LABEL maintainer="SC Clouds <contato@scclouds.com.br> (@scclouds)"

RUN apt-get update -y && \
    DEBIAN_FRONTEND=noninteractive TZ=Etc/UTC \
    apt-get install -y --no-install-recommends \
        tzdata \
        make \
        locate \
        tar \
        lsb-release \
        build-essential \
        dpkg-dev \
        devscripts \
        debhelper \
        genisoimage \
        git \
        maven \
        openjdk-11-jdk \
        python \
        python3 \
        python3-mysqldb \
        python3-mysql.connector \
        dh-systemd \
        python3-setuptools \
        python-setuptools \
        curl \
        wget \
        sudo && \
    curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash - && \
    apt-get install -y --no-install-recommends \
        nodejs && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    update-java-alternatives -s java-1.11.0-openjdk-amd64

ENV JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64

VOLUME /mnt/build
WORKDIR /mnt/build

COPY docker-entrypoint.sh /usr/local/bin/docker-entrypoint.sh
COPY environment-info.sh /usr/local/bin/environment-info.sh

ENTRYPOINT ["docker-entrypoint.sh"]
