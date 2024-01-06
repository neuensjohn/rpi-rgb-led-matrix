set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)

set(SOURCES
    gpio.cc
    led-matrix.cc
    options-initialize.cc
    framebuffer.cc
    thread.cc
    bdf-font.cc
    graphics.cc
    led-matrix-c.cc
    hardware-mapping.c
    pixel-mapper.cc
    multiplex-mappers.cc
    content-streamer.cc
)

set(INTERNAL_HEADERS
    framebuffer-internal.h
    gpio-bits.h
    gpio.h
    hardware-mapping.h
    multiplex-mappers-internal.h
    utf8-internal.h
)

add_library(${PROJECT_NAME} STATIC 
    ${SOURCES} 
    ${INTERNAL_HEADERS}
)

target_link_libraries(${PROJECT_NAME} PRIVATE
    Threads::Threads
)

target_include_directories(${PROJECT_NAME} PUBLIC 
    ../include
)

include_directories(../include)