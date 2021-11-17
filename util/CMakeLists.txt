set(SRC_UTIL src)

aux_source_directory(${SRC_UTIL} SRC_UTIL_ALL)
add_library(wcdb_util STATIC ${SRC_UTIL_ALL})
target_include_directories(wcdb_util 
PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include 
PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/../abstract/include)

