cmake_minimum_required(VERSION 3.20)

project(setting-up-sfml-with-fetch-content)
# USE the WIN32 key to hide the console like this:
# add_executable(app WIN32)
add_executable(app)

option(BUILD_SHARED_LIBS "Build shared libraries" OFF)

target_sources(app
PRIVATE
    src/main.cpp
)

include(FetchContent)
FetchContent_Declare(SFML
    GIT_REPOSITORY https://github.com/SFML/SFML.git
    GIT_TAG 2.6.x
    GIT_SHALLOW ON
    EXCLUDE_FROM_ALL
    SYSTEM)
FetchContent_MakeAvailable(SFML)

# find_package(SFML REQUIRED COMPONENTS System Window Graphics)
# target_link_libraries(app PRIVATE SFML::System SFML::Window SFML::Graphics)

target_link_libraries(app PRIVATE sfml-graphics)
target_compile_features(app PRIVATE cxx_std_17)

# target_link_options(app PRIVATE -static)
