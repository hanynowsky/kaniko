# Copyright 2018 Google, Inc. All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# Builds the static Go image to execute in a Kubernetes job

FROM scratch
ADD out/executor /kaniko/executor
ADD files/ca-certificates.crt /kaniko/ssl/certs/
ADD files/docker-credential-gcr /usr/local/bin/
ADD files/config.json /root/.docker/
RUN ["docker-credential-gcr", "config", "--token-source=env"]
ENV HOME /root
ENV PATH /usr/local/bin
ENV SSL_CERT_DIR=/kaniko/ssl/certs
ENTRYPOINT ["/kaniko/executor"]
