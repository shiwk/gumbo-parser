# Gumbo Parser CMake configuration
set(CMAKE_C_COMPILER clang)
file(GLOB HEADERS ${CMAKE_CURRENT_SOURCE_DIR}/src/*.h)
file(GLOB SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/src/*.c)

add_library(gumbo  ${SOURCES} ${HEADERS})
# set_target_properties(gumbo PROPERTIES LINKER_LANGUAGE C)

target_include_directories(gumbo PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/src)
target_compile_options(gumbo PRIVATE -Wno-unused-parameter)

if(MSVC)
    target_compile_options(gumbo PRIVATE /W4)
else()
    target_compile_options(gumbo PRIVATE -Wall -Wextra)
endif()
