cmake_minimum_required( VERSION 3.16...4.2 FATAL_ERROR )

set ( SOURCES
    "vendor/glad/src/gl.c"
    "worldapp/src/main.cpp"
)

project( "3DWORLD" )

# OPTIONS
set( GLFW_BUILD_DOCS OFF CACHE BOOL "GLFW lib only")
set( GLFW_INSTALL OFF CACHE BOOL "GLFW lib only")

add_executable( ${PROJECT_NAME} "worldapp/src/main.cpp" )

target_sources( ${PROJECT_NAME} 
    PRIVATE
        ${SOURCES}
)
target_include_directories( ${PROJECT_NAME} 
    PRIVATE
    "${PROJECT_SOURCE_DIR}/worldapp/include"
    "${PROJECT_SOURCE_DIR}/vendor/glfw/include"
    "${PROJECT_SOURCE_DIR}/vendor/glad/include"
    "${PROJECT_SOURCE_DIR}/vendor/glm"
)

add_subdirectory( vendor/glfw )
target_link_libraries( ${PROJECT_NAME} glfw )