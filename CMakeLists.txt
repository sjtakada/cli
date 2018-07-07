cmake_minimum_required(VERSION 2.8)
project(CLI)

#set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -D_GLIBCXX_USE_CXX11_ABI=0 -std=c++11")
#set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}")

set(CMAKE_CXX_STANDARD 11)

set(SOURCE
  src/cli_action.cpp
  src/cli_builtins.cpp
  src/cli.cpp
  src/cli_http.cpp
  src/cli_readline.cpp
  src/cli_string.cpp
  src/cli_tree.cpp
  src/cli_utils.cpp
  src/main.cpp
  )

find_package(CURL REQUIRED)
#find_package(JSONCPP REQUIRED)

#pkg_check_modules(JSONCPP jsoncpp)

find_library(LIBJSONCPP libjsoncpp.so)
find_library(LIBREADLINE libreadline.so)
find_library(LIBTINFO libtinfo.so)
find_library(LIBCURLPP libcurlpp.so)
find_library(LIBCURL libcurl.so)
find_library(LIBZ libz.so)
find_library(LIBSSL libssl.so)
find_library(LIBGSSAPI libgssapi_krb5.so)
find_library(LIBCRYPTO libcrypto.so)
find_library(LIBTHREAD libpthread_nonshared.a)
add_executable(cli ${SOURCE})
target_link_libraries(cli
  ${LIBJSONCPP} ${LIBREADLINE} ${LIBTINFO}
  ${LIBCURLPP} ${LIBCURL} ${LIBZ}
  ${LIBSSL} ${LIBGSSAPI} ${LIBCRYPTO}
  ${LIBPTHREAD}
  )
