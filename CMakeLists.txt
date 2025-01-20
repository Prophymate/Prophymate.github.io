cmake_minimum_required (VERSION 3.8)

if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("CMakeNinja")

file(GLOB ALL_HEADERS "include/*.h")
file(GLOB ALL_SRC "src/*.cpp")

find_package(SFML REQUIRED COMPONENTS graphics window system)

add_executable(CMakeNinja ${ALL_SRC})
target_include_directories(CMakeNinja PUBLIC ${ALL_HEADERS})
target_compile_features(CMakeNinja PUBLIC cxx_std_20)


#target_link_libraries(CMakeNinja sfml-graphics sfml-window sfml-system)
