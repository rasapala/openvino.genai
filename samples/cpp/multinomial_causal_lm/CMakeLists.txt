# Copyright (C) 2023-2024 Intel Corporation
# SPDX-License-Identifier: Apache-2.0

find_package(OpenVINOGenAI REQUIRED PATHS
    "${CMAKE_BINARY_DIR}"  # Reuse the package from the build.
    ${OpenVINO_DIR}  # GenAI may be installed alogside OpenVINO.
)
add_executable(multinomial_causal_lm multinomial_causal_lm.cpp)
target_link_libraries(multinomial_causal_lm PRIVATE openvino::genai)
target_compile_features(greedy_causal_lm PRIVATE cxx_std_17)
install(TARGETS multinomial_causal_lm
    RUNTIME DESTINATION samples_bin/
    COMPONENT samples_bin
    EXCLUDE_FROM_ALL)
