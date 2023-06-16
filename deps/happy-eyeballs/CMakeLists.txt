cmake_minimum_required(VERSION 3.16...3.25)

add_library(happy-eyeballs STATIC EXCLUDE_FROM_ALL)
add_library(OBS::happy-eyeballs ALIAS happy-eyeballs)

target_sources(happy-eyeballs
  PRIVATE
    happy-eyeballs.c
  PUBLIC
    happy-eyeballs.h
  )

target_include_directories(happy-eyeballs PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

target_link_libraries(happy-eyeballs PUBLIC OBS::libobs)

if(OS_WINDOWS)
  target_link_libraries(happy-eyeballs PUBLIC OBS::w32-pthreads)
endif()

set_target_properties(happy-eyeballs PROPERTIES FOLDER deps)
