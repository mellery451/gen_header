project(foo)

add_custom_command(
    OUTPUT ${CMAKE_BINARY_DIR}/tab.h
    COMMAND awk -f ${CMAKE_SOURCE_DIR}/util/mktab > ${CMAKE_BINARY_DIR}/tab.h
    WORKING_DIRECTORY ${CMAKE_BINARY_DIR})

add_executable(foo_exe src/foo.c ${CMAKE_BINARY_DIR}/tab.h)

target_include_directories(foo_exe PUBLIC ${CMAKE_BINARY_DIR})
