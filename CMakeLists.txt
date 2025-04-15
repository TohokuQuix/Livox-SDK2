cmake_minimum_required(VERSION 3.5)
project(livox_sdk2_ros)

# ament_cmakeの利用宣言
find_package(ament_cmake REQUIRED)

set(CMAKE_CXX_STANDARD 11)

message(STATUS "main project dir: ${PROJECT_SOURCE_DIR}")

if(CMAKE_CROSSCOMPILING)
  set(THREADS_PTHREAD_ARG "PLEASE_FILL_OUT-FAILED_TO_RUN"
      CACHE STRING "Result from TRY_RUN" FORCE)
endif()

if(UNIX)
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread")
endif()

# Livox-SDK2のサブディレクトリを追加
add_subdirectory(sdk_core)
add_subdirectory(samples)

# 必要なファイルやディレクトリのインストール設定
install(DIRECTORY include/ DESTINATION include)

# amentパッケージとして登録
ament_package()
