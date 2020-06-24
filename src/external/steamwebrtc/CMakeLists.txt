include_directories(${CMAKE_SOURCE_DIR}/webrtc/include)
link_directories(
    ${CMAKE_SOURCE_DIR}/webrtc/lib
)
include_directories(
    ${CMAKE_SOURCE_DIR}/webrtc/include/webrtc
    ${CMAKE_SOURCE_DIR}/webrtc/include/webrtc/third_party/abseil-cpp
)
link_directories(${CMAKE_SOURCE_DIR}/webrtc/lib)

add_library(steamwebrtc SHARED
    "ice_session.h"
    "steamwebrtc_internal.h"
    "ice_session.cpp"
)
target_link_libraries(steamwebrtc PUBLIC webrtc Winmm Secur32 Iphlpapi)

set_property(TARGET steamwebrtc PROPERTY
             MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
