project(pvr.njoy)

cmake_minimum_required(VERSION 2.6)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${PROJECT_SOURCE_DIR})

enable_language(CXX)

option(PACKAGE_ZIP "Package Zip file?" OFF)

find_package(TinyXML REQUIRED)
find_package(xbmc REQUIRED)
find_package(xbmcplatform REQUIRED)

include_directories(${xbmcplatform_INCLUDE_DIRS}
                    ${TINYXML_INCLUDE_DIR}
                    ${XBMC_INCLUDE_DIR})

set(NJOY_SOURCES src/client.cpp
                 src/N7Xml.cpp)

set(DEPLIBS ${xbmcplatform_LIBRARIES}
            ${TINYXML_LIBRARIES})

build_addon(pvr.njoy NJOY DEPLIBS)

include(CPack)
