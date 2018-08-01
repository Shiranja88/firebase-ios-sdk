# Copyright 2018 Google
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

if(NOT FUZZING)
  return()
endif()

# TODO(minafarid): Currently we support local fuzzing only where we build
# libFuzzer. Future plans include integrating into OSS Fuzz, where the fuzzing
# library is already provided.
find_package(LibFuzzer REQUIRED)

cc_binary(
  firebase_firestore_fuzzing_serializer
  SOURCES
    fuzz_test_serializer.cc
  DEPENDS
    LibFuzzer
    firebase_firestore_remote
)