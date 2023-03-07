# CMakeLists.txt

# Minimum required version of CMake
cmake_minimum_required(VERSION 3.22)

# Project name
project(ALT-A0)

add_subdirectory(Drivers)
set(CMAKE_C_COMPILER ${CMAKE_SOURCE_DIR}/msp430-gcc-9.3.1.11_linux64/bin/msp430-elf-gcc)

# Sources
set(SRC_DIR src)
set(SRC_DIR_DRIVERS Drivers/src)

set(SOURCES
    ${SRC_DIR}/Alt_Appl.c
)

# Include directories
include_directories(
                    include
                    )
include_directories(${Drivers_INCLUDE_DIRS})

# Compiler definitions
# add_definitions(-DPORT1_VECTOR_ISR)

# Compiler flags
set(CMAKE_C_STANDARD 99)
set(CMAKE_C_FLAGS "-mmcu=msp430g2553 -O2 -g -Wall")

# Linker flags
set(CMAKE_EXE_LINKER_FLAGS "-L ../linker -T ../linker/lnk_msp430g2553.cmd")

# Add executable
add_executable(ALTA0.out ${SOURCES})
target_link_libraries(ALTA0.out Drivers)

