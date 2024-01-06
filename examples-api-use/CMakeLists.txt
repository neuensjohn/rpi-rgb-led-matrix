
project(examples)


add_definitions( -DMAGICKCORE_QUANTUM_DEPTH=16 )
add_definitions( -DMAGICKCORE_HDRI_ENABLE=0 )
find_package(ImageMagick COMPONENTS Magick++)
if(ImageMagick_FOUND)
    add_executable(image-example image-example.cc)
    target_link_libraries(image-example rgbmatrix ${ImageMagick_LIBRARIES})
    target_include_directories(image-example PRIVATE rgbmatrix ${ImageMagick_INCLUDE_DIRS})

else()
    message(WARNING "image-example will not be built. Magick++ library not found.")
endif()

add_executable(c-example c-example.c)
target_link_libraries(c-example rgbmatrix)
target_include_directories(c-example PRIVATE rgbmatrix)

add_executable(demo demo-main.cc)
target_link_libraries(demo rgbmatrix)
target_include_directories(demo PRIVATE rgbmatrix)

add_executable(minimal-example minimal-example.cc) 
target_link_libraries(minimal-example rgbmatrix)
target_include_directories(minimal-example PRIVATE rgbmatrix)

add_executable(text-example text-example.cc) 
target_link_libraries(text-example rgbmatrix)
target_include_directories(text-example PRIVATE rgbmatrix)

add_executable(scrolling-text-example scrolling-text-example.cc) 
target_link_libraries(scrolling-text-example rgbmatrix)
target_include_directories(scrolling-text-example PRIVATE rgbmatrix)

add_executable(clock clock.cc) 
target_link_libraries(clock rgbmatrix)
target_include_directories(clock PRIVATE rgbmatrix)

add_executable(ledcat ledcat.cc) 
target_link_libraries(ledcat rgbmatrix)
target_include_directories(ledcat PRIVATE rgbmatrix)

add_executable(input-example input-example.cc) 
target_link_libraries(input-example rgbmatrix)
target_include_directories(input-example PRIVATE rgbmatrix)

add_executable(pixel-move pixel-mover.cc)
target_link_libraries(pixel-move rgbmatrix)
target_include_directories(pixel-move PRIVATE rgbmatrix)

