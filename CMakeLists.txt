# Copyright 2020 The RacyDB Authors. All rights reserved.
# Use of this source code is governed by a Apache-style license that can be
# found in the LICENSE file. See the AUTHORS file for names of contributors.

cmake_minimum_required(VERSION 3.9)
# Keep the version below in sync with the one in db.h
project(racydb VERSION 0.0.1 LANGUAGES C CXX)

# C standard can be overridden when this is used as a sub-project.
if(NOT CMAKE_C_STANDARD)
  # This project can use C11, but will gracefully decay down to C89.
  set(CMAKE_C_STANDARD 11)
  set(CMAKE_C_STANDARD_REQUIRED OFF)
  set(CMAKE_C_EXTENSIONS OFF)
endif(NOT CMAKE_C_STANDARD)

# C++ standard can be overridden when this is used as a sub-project.
if(NOT CMAKE_CXX_STANDARD)
  # This project requires C++11.
  set(CMAKE_CXX_STANDARD 11)
  set(CMAKE_CXX_STANDARD_REQUIRED ON)
  set(CMAKE_CXX_EXTENSIONS OFF)
endif(NOT CMAKE_CXX_STANDARD)

if (WIN32)
  set(RACYDB_PLATFORM_NAME RACYDB_PLATFORM_WINDOWS)
  add_definitions(-D_UNICODE -DUNICODE)
else (WIN32)
  set(RACYDB_PLATFORM_NAME RACYDB_PLATFORM_POSIX)
endif (WIN32)

option(RACYDB_BUILD_TESTS "Build RacyDB's unit tests" ON)
option(RACYDB_BUILD_BENCHMARKS "Build RacyDB's benchmarks" ON)
option(RACYDB_INSTALL "Install RacyDB's header and library" ON)