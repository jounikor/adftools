#
#

cmake_minimum_required(VERSION 3.10)

#

# set the project name
project(adftools VERSION 0.3 LANGUAGES C)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_BINARY_DIR}/build)

if (DEFINED CMAKE_BUILD_TYPE)
	message(STATUS "Build type define as ${CMAKE_BUILD_TYPE}")
	if (CMAKE_BUILD_TYPE MATCHES Release)
		set(CMAKE_C_FLAGS_RELEASE "${CMAKE_C_FLAGS_RELEASE} -O3")
	else()
		set(CMAKE_C_FLAGS_DEBUG "${CMAKE_C_FLAGS_DEBUG} -g")
	endif()
endif()


# libadf settings
set(NATIV_DIR generic)

add_subdirectory(
	adflib
)

# Common files for the adftools
set(COMMON_SRC error.c misc.c zfile.c bootblocks.c version.c)

add_executable(adfcopy adfcopy.c 	${COMMON_SRC})
add_executable(adfdelete adfdelete.c 	${COMMON_SRC})
add_executable(adfextract adfextract.c 	${COMMON_SRC})
add_executable(adfinstall adfinstall.c 	${COMMON_SRC})
add_executable(adfmakedir adfmakedir.c 	${COMMON_SRC})
add_executable(adfcreate adfcreate.c 	${COMMON_SRC})
add_executable(adfdump adfdump.c 	${COMMON_SRC})
add_executable(adfinfo adfinfo.c 	${COMMON_SRC})
add_executable(adflist adflist.c 	${COMMON_SRC})

#configure_file(foo.h.in foo.h)

target_link_libraries(adfcopy 		PUBLIC adf)
target_link_libraries(adfdelete		PUBLIC adf)
target_link_libraries(adfextract	PUBLIC adf)
target_link_libraries(adfinstall	PUBLIC adf)
target_link_libraries(adfmakedir	PUBLIC adf)
target_link_libraries(adfcreate		PUBLIC adf)
target_link_libraries(adfdump		PUBLIC adf)
target_link_libraries(adfinfo		PUBLIC adf)
target_link_libraries(adflist		PUBLIC adf)

target_include_directories(adfcopy 	PUBLIC "${PROJECT_BINARY_DIR}" "${PROJECT_SOURCE_DIR}" "${PROJECT_SOURCE_DIR}/adflib")
target_include_directories(adfdelete 	PUBLIC "${PROJECT_BINARY_DIR}" "${PROJECT_SOURCE_DIR}" "${PROJECT_SOURCE_DIR}/adflib")
target_include_directories(adfextract 	PUBLIC "${PROJECT_BINARY_DIR}" "${PROJECT_SOURCE_DIR}" "${PROJECT_SOURCE_DIR}/adflib")
target_include_directories(adfinstall 	PUBLIC "${PROJECT_BINARY_DIR}" "${PROJECT_SOURCE_DIR}" "${PROJECT_SOURCE_DIR}/adflib")
target_include_directories(adfmakedir 	PUBLIC "${PROJECT_BINARY_DIR}" "${PROJECT_SOURCE_DIR}" "${PROJECT_SOURCE_DIR}/adflib")
target_include_directories(adfcreate	PUBLIC "${PROJECT_BINARY_DIR}" "${PROJECT_SOURCE_DIR}" "${PROJECT_SOURCE_DIR}/adflib")
target_include_directories(adfdump 	PUBLIC "${PROJECT_BINARY_DIR}" "${PROJECT_SOURCE_DIR}" "${PROJECT_SOURCE_DIR}/adflib")
target_include_directories(adfinfo 	PUBLIC "${PROJECT_BINARY_DIR}" "${PROJECT_SOURCE_DIR}" "${PROJECT_SOURCE_DIR}/adflib")
target_include_directories(adflist 	PUBLIC "${PROJECT_BINARY_DIR}" "${PROJECT_SOURCE_DIR}" "${PROJECT_SOURCE_DIR}/adflib")

