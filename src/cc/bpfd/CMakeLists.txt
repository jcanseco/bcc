# Copyright (c) Jazel Canseco, 2018
# Licensed under the Apache License, Version 2.0 (the "License")
cmake_minimum_required(VERSION 2.8.7)

project(bpfd)

include_directories(..)
include_directories(../compat)

add_library(bpfd-bpf ../libbpf.c ../perf_reader.c)

add_executable(bpfd bpfd.c base64.c remote_perf_reader.c utils.c)
target_link_libraries(bpfd bpfd-bpf)
