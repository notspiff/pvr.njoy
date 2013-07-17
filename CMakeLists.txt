PROJECT(pvr.njoy)

CMAKE_MINIMUM_REQUIRED(VERSION 2.6)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${PROJECT_SOURCE_DIR})

ENABLE_LANGUAGE(CXX)

OPTION(PACKAGE_ZIP "Package Zip file?" OFF)

FIND_PACKAGE(TinyXML REQUIRED)
FIND_PACKAGE(xbmc REQUIRED)
FIND_PACKAGE(xbmcplatform REQUIRED)

addon_version(pvr.njoy NJOY)

INCLUDE_DIRECTORIES(${xbmcplatform_INCLUDE_DIRS}
                    ${TINYXML_INCLUDE_DIR}
                    ${XBMC_INCLUDE_DIR})

SET(SOURCES src/client.cpp
            src/N7Xml.cpp)

SET(DEPLIBS ${xbmcplatform_LIBRARIES}
            ${TINYXML_LIBRARIES})

build_addon(pvr.njoy SOURCES DEPLIBS NJOY_VERSION)
install_addon(pvr.njoy ${NJOY_VERSION})
