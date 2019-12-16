# Copyright 2019 The Mumble Developers. All rights reserved.
# Use of this source code is governed by a BSD-style license
# that can be found in the LICENSE file at the root of the
# Mumble source tree or at <https://www.mumble.info/LICENSE>.

# Overlay payload for Unix-like systems.

add_library(overlay_gl SHARED "overlay.c")

set_target_properties(overlay_gl PROPERTIES VERSION ${CMAKE_PROJECT_VERSION})

if(UNIX AND NOT APPLE)
	set_target_properties(overlay_gl PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
	set_target_properties(overlay_gl PROPERTIES OUTPUT_NAME "mumble")

	target_compile_definitions(overlay_gl PRIVATE "TARGET_UNIX")
endif()
