# Some compilers warn that the return value of cr_assert gets converted from an
# int to a unsigned char:1. To avoid this error in those compilers, turn off
# conversion warnings for test code.
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wno-conversion")

list(APPEND CMAKE_CTEST_ARGUMENTS --verbose)

# If you need to test a library called foo, use lines like the following.
add_executable(test_lexer test_lexer.c)
target_link_libraries(test_lexer
    PRIVATE lexer
    PUBLIC ${CRITERION}
)
add_test(
    NAME test_lexer
    COMMAND test_lexer ${CRITERION_FLAGS}
)
