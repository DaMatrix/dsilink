cmake_minimum_required(VERSION 3.15)
project(dsilink)

set(CMAKE_CXX_STANDARD 17)

add_subdirectory(lib/PorkLib_cpp)

add_executable(dsilink "")
set_target_properties(dsilink PROPERTIES LINKER_LANGUAGE CXX)

file(GLOB_RECURSE sources CONFIGURE_DEPENDS "${CMAKE_CURRENT_LIST_DIR}/source/*.cpp" "${CMAKE_CURRENT_LIST_DIR}/source/*.h" "${CMAKE_CURRENT_LIST_DIR}/source/*.S")
file(GLOB_RECURSE headers CONFIGURE_DEPENDS "${CMAKE_CURRENT_LIST_DIR}/include/*.h")
target_sources(dsilink PRIVATE ${sources} PUBLIC ${headers})

target_link_libraries(dsilink porklib_cpp)
