# Wymagana minimalna wersja CMake
cmake_minimum_required(VERSION 3.10)

# Nazwa projektu i język
project(NumLibProject CXX)

# Ustawienie standardu C++ na C++17
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# --- 1. Definicja biblioteki ---
file(GLOB_RECURSE LIB_SOURCES "src/*.cpp")
add_library(NumLib STATIC ${LIB_SOURCES})
target_include_directories(NumLib PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/include")


# --- 2. Definicja programu z przykładami ---
add_executable(ExamplesApp examples/example_runner.cpp)
target_link_libraries(ExamplesApp PRIVATE NumLib)


# --- 3. Definicja programu z testami ---
add_executable(TestsApp tests/test_runner.cpp)
target_link_libraries(TestsApp PRIVATE NumLib)