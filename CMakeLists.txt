cmake_minimum_required(VERSION 3.10)
project(BigBean)

# Set the C++ standard
set(CMAKE_CXX_STANDARD 17)

# Include directories
include_directories(include)

# Add the source files
set(SOURCES
    src/main.cpp
    src/board.cpp
    src/movegen.cpp
    src/utils.cpp
    src/gameState.cpp
    src/evaluation.cpp
    src/search.cpp
)

# List of test source files (one per test)
set(TEST_FILES
    tests/board_test.cpp
    tests/pawn_test.cpp
    tests/slidingPiece_test.cpp
    tests/specialPiece_test.cpp
    tests/gameState_test.cpp
    tests/evaluation_test.cpp
    tests/minimax_test.cpp
)

# For each test file, create a separate executable
foreach(test_src ${TEST_FILES})
    # Get the filename without extension for the executable name
    get_filename_component(test_name ${test_src} NAME_WE)
    add_executable(${test_name} ${test_src}
        src/board.cpp
        src/movegen.cpp
        src/utils.cpp
        src/gameState.cpp
        src/evaluation.cpp
        src/search.cpp
    )
    target_include_directories(${test_name} PRIVATE include)
endforeach()

# Add the executable for the main program
add_executable(BigBean ${SOURCES})