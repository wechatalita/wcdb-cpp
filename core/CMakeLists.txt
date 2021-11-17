cmake_minimum_required (VERSION 3.8.10)
set(SRC_CORE src)

aux_source_directory(${SRC_CORE} SRC_CORE_ALL)
add_library(wcdb_core  STATIC ${SRC_CORE_ALL})
target_include_directories(wcdb_core
        PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include
        PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/../abstract/include
        PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/../repair/include
        PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/../sqlcipher/include
	PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/../util/include
        )

if(LINUX)
	message("link with pthread on linux")
	target_link_libraries(wcdb_core  -Wl,--start-group wcdb_util wcdb_abstract wcdb_repair wcdb_sqlcipher pthread -Wl,--end-group)


else()
	target_link_libraries(wcdb_core wcdb_util wcdb_abstract wcdb_repair)
endif()


