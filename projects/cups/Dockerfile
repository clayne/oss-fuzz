# Copyright 2022 Google LLC
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
################################################################################
FROM gcr.io/oss-fuzz-base/base-builder
RUN apt-get update && apt-get install -y zlib1g-dev libavahi-client-dev libsystemd-dev
RUN git clone --depth 1 https://github.com/OpenPrinting/cups
RUN git clone --depth 1 https://github.com/OpenPrinting/fuzzing.git
RUN cp $SRC/fuzzing/projects/cups/oss_fuzz_build.sh $SRC/build.sh
COPY run_tests.sh *.diff $SRC/
RUN cd $SRC/fuzzing && git apply $SRC/test_patch.diff
WORKDIR $SRC/cups
