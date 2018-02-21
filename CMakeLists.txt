cmake_minimum_required(VERSION 3.9)
project(ODDRVIDV)

set(CMAKE_CXX_STANDARD 11)



if (WIN32)
    set(BOOST_ROOT "C:/boost_1_66_0/")
    set(Boost_USE_STATIC_LIBS ON)
    set(Boost_USE_MULTITHREAD ON)

    include_directories(${BOOST_ROOT})
    link_directories(${BOOST_ROOT}/stage/lib) # add this before add_executable()
endif()

add_executable(ODDRVIDV main.cpp)

if(NOT MSVC)
    find_package(Boost)

    if (Boost_FOUND)
        include_directories(${Boost_INCLUDE_DIRS})
        target_link_libraries(ODDRVIDV ${Boost_LIBRARIES})
    endif()
endif()