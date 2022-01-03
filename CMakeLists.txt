cmake_minimum_required(VERSION 3.18)

# uncomment these 2 lines if using clang
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -target x86_64-pc-windows-gnu")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -target x86_64-pc-windows-gnu")

if (NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if (NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 90)
endif()

project("v8-playground")

include_directories("C:/Users/Administrator/Downloads/v8_engine_9.2.230.22/headers")
link_directories("C:/Users/Administrator/Downloads/v8_engine_9.2.230.22/windows")

add_library(v8 STATIC IMPORTED GLOBAL)
set_target_properties(v8 PROPERTIES IMPORTED_LOCATION "C:/Users/Administrator/Downloads/v8_engine_9.2.230.22/windows/v8.dll.lib")

ADD_LIBRARY(v8_libplatform STATIC IMPORTED GLOBAL)
set_target_properties(v8_libplatform PROPERTIES IMPORTED_LOCATION "C:/Users/Administrator/Downloads/v8_engine_9.2.230.22/windows/v8_libplatform.dll.lib")

ADD_LIBRARY(v8_libbase STATIC IMPORTED GLOBAL)
set_target_properties(v8_libbase PROPERTIES IMPORTED_LOCATION "C:/Users/Administrator/Downloads/v8_engine_9.2.230.22/windows/v8_libbase.dll.lib")

ADD_LIBRARY(icui18n STATIC IMPORTED GLOBAL)
set_target_properties(icui18n PROPERTIES IMPORTED_LOCATION "C:/Users/Administrator/Downloads/v8_engine_9.2.230.22/windows/icui18n.dll.lib")

ADD_LIBRARY(icuuc STATIC IMPORTED GLOBAL)
set_target_properties(icuuc PROPERTIES IMPORTED_LOCATION "C:/Users/Administrator/Downloads/v8_engine_9.2.230.22/windows/icuuc.dll.lib")

ADD_LIBRARY(zlib STATIC IMPORTED GLOBAL)
set_target_properties(zlib PROPERTIES IMPORTED_LOCATION "C:/Users/Administrator/Downloads/v8_engine_9.2.230.22/windows/zlib.dll.lib")

ADD_LIBRARY(torque STATIC IMPORTED GLOBAL)
set_target_properties(torque PROPERTIES IMPORTED_LOCATION "C:/Users/Administrator/Downloads/v8_engine_9.2.230.22/windows/torque.lib")


add_executable(${PROJECT_NAME}
    "src/main.cpp"
)

target_link_libraries(${PROJECT_NAME} PRIVATE
    v8 
    v8_libplatform 
    v8_libbase 
    icui18n 
    icuuc 
    torque
    zlib
)
