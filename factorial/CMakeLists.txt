project(factorial CXX)

add_library(factorial STATIC src/factorial.cpp)
target_include_directories(factorial PUBLIC include)

if(ENABLE_TESTS)
	add_executable(factorial_test tests/factorial.cpp)
	target_include_directories(factorial_test PRIVATE factorial)
	target_link_libraries(factorial_test factorial ${GTEST_LDFLAGS})
	target_compile_options(factorial_test PUBLIC ${GTEST_CFLAGS})

	add_test(NAME test_factorial COMMAND factorial_test)
endif()
