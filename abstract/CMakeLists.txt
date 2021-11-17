set(SRC_ABSTRACT src)
set(CMAKE_POSITION_INDEPENDENT_CODE ON)
aux_source_directory(${SRC_ABSTRACT} SRC_ABSTRACT_ALL)
add_library(wcdb_abstract STATIC ${SRC_ABSTRACT_ALL})
target_include_directories(wcdb_abstract
        PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include
        PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/../..
        PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/../util/include
        PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/../repair/include
        PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/../sqlcipher/include
        )

target_link_libraries(wcdb_abstract wcdb_util wcdb_repair wcdb_sqlcipher)