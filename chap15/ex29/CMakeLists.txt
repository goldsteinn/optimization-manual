set(avx_ex29_srcs ex29_test.cpp sqrt_rsqrtps_sse.c sqrt_vrsqrtps_avx.c)
if(CMAKE_CXX_COMPILER_ID MATCHES Clang OR CMAKE_CXX_COMPILER_ID MATCHES GNU OR CMAKE_CXX_COMPILER_ID MATCHES AppleClang)
set(avx_ex29_srcs ${avx_ex29_srcs} sqrt_rsqrtps_sse.s sqrt_vrsqrtps_avx.s)
elseif(MSVC)
set(avx_ex29_srcs ${avx_ex29_srcs} sqrt_rsqrtps_sse.asm sqrt_vrsqrtps_avx.asm)
endif()
add_executable(avx_ex29_tests ${avx_ex29_srcs})

target_link_libraries(avx_ex29_tests gtest_main)
add_test(NAME avx_ex29_test COMMAND avx_ex29_tests)
