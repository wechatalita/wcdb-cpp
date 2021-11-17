cmake_minimum_required(VERSION 3.8.10)
set(SRC_REPAIR src)
aux_source_directory(${SRC_REPAIR} SRC_REPAIR_ALL)
add_library(wcdb_repair STATIC ${SRC_REPAIR_ALL})

if(LINUX)
	message("include openssl in repair")
	target_include_directories(wcdb_repair 
	PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)

elseif(ANDROID)
	message("include openssl in repair")
	target_include_directories(wcdb_repair 
	PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)

else()
	target_include_directories(wcdb_repair PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)
endif()

target_link_libraries(wcdb_repair wcdb_sqlcipher -lz)