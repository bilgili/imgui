# Copyright (c) RealV Authors. All rights reserved.
# This code is licensed under the MIT License, see LICENSE.

set(IMGUI_LIB_PUBLIC_HEADERS
  imgui.h
  imstb_rectpack.h
  imstb_textedit.h
  imstb_truetype.h
  )

set(IMGUI_LIB_PRIVATE_HEADERS
  imgui_internal.h
  )

set(IMGUI_LIB_SOURCES
  imgui.cpp
  imgui_draw.cpp
  imgui_widgets.cpp
  )

add_library(imgui_lib SHARED ${IMGUI_LIB_PUBLIC_HEADERS} ${IMGUI_LIB_PRIVATE_HEADERS} ${IMGUI_LIB_SOURCES})

target_include_directories(imgui_lib PUBLIC
    $<BUILD_INTERFACE:${CMAKE_SOURCE_DIR}/modules/imgui>
    $<INSTALL_INTERFACE:${YOUR_INSTALL_DIR}/lib1>
)

set(IMGUI_GLFW_PUBLIC_HEADERS
  examples/imgui_impl_glfw.h
  )

set(IMGUI_GLFW_SOURCES
  examples/imgui_impl_glfw.cpp
  )

add_library(imgui_glfw SHARED ${IMGUI_GLFW_PUBLIC_HEADERS} ${IMGUI_GLFW_SOURCES})
target_link_libraries(imgui_glfw PUBLIC imgui_lib glfw)

