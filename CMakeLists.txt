CMAKE_MINIMUM_REQUIRED(VERSION 3.11 FATAL_ERROR)
if(COMMAND cmake_policy)
	cmake_policy(SET CMP0003 NEW)
endif(COMMAND cmake_policy)

project(TinyFileDialogs)

set(CMAKE_CXX_STANDARD 17)

option(ENABLE_TFD_STATIC "Build static (.a) library" OFF)

add_library(TinyFileDialogs SHARED "tinyfiledialogs.c" "tinyfiledialogs.h")

install(TARGETS "TinyFileDialogs" LIBRARY DESTINATION lib PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE)

if(ENABLE_TFD_STATIC)
    add_library(TinyFileDialogs-static STATIC "tinyfiledialogs.c" "tinyfiledialogs.h")
    set_target_properties(TinyFileDialogs-static PROPERTIES OUTPUT_NAME "TinyFileDialogs")
    install(TARGETS "TinyFileDialogs-static" ARCHIVE DESTINATION lib)
endif(ENABLE_TFD_STATIC)

install(FILES "tinyfiledialogs.h" DESTINATION include)

