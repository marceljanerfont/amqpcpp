cmake_minimum_required (VERSION 2.6)

# project
project (amqpcpp)
add_subdirectory(src)


#include_directories("$ENV{APIS_PATH}/openssl-1.0.2l/include")
#if(CMAKE_BUILD_TYPE EQUAL "Debug")
#    message("debug mode!!")
#    link_directories( "$ENV{APIS_PATH}/openssl-1.0.2l/libd")
#else()
#     message("release mode!")
#    link_directories( "$ENV{APIS_PATH}/openssl-1.0.2l/lib")
#endif()
#set(LIBS ${LIBS} libeay32 ssleay32)



include_directories("${CMAKE_CURRENT_SOURCE_DIR}/include")
file(GLOB SRCS "${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp")
message("Sources: ${SRCS}")

message("OPENSSL_ROOT_DIR: ${OPENSSL_ROOT_DIR}")
message("OPENSSL_LIBRARIES: ${OPENSSL_LIBRARIES}")
message("RABBITMQ_ROOT_DIR: ${RABBITMQ_ROOT_DIR}")
message("RABBITMQ_LIBRARY: ${RABBITMQ_LIBRARY}")

include_directories("${OPENSSL_ROOT_DIR}/include")
include_directories("${RABBITMQ_ROOT_DIR}/include")

add_library(amqpcpp STATIC "${SRCS}")


# target_link_libraries(hello hello_lib)

# gtest
# add_executable(run_tests test_hello.cpp)
# target_link_libraries(run_tests hello_lib gtest gtest_main)
#target_link_libraries(run_tests gtest gtest_main)
