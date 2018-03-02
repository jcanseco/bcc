# Copyright (c) Jazel Canseco, 2018
# Licensed under the Apache License, Version 2.0 (the "License")

add_library(bpfd-bpf ../libbpf.c ../perf_reader.c)

add_library(bpfd-bcc ../bcc_elf.c ../bcc_perf_map.c ../bcc_proc.c ../bcc_syms.cc ../ns_guard.cc ../common.cc ../vendor/tinyformat.hpp)
target_link_libraries(bpfd-bcc ${LIBELF_LIBRARIES})

add_executable(bpfd bpfd.c base64.c remote_perf_reader.c utils.c)
target_link_libraries(bpfd bpfd-bpf)
target_link_libraries(bpfd bpfd-bcc)
