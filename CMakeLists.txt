cmake_minimum_required(VERSION 3.1.0)
project(lua-enet)

add_subdirectory(enet)
set_target_properties(enet PROPERTIES POSITION_INDEPENDENT_CODE TRUE)

add_library(lua-enet MODULE enet.c)
set_target_properties(lua-enet PROPERTIES WINDOWS_EXPORT_ALL_SYMBOLS TRUE)
target_include_directories(lua-enet PRIVATE enet/include)
target_link_libraries(lua-enet enet)

if(WIN32)
  target_link_libraries(lua-enet ws2_32 winmm)
endif()
