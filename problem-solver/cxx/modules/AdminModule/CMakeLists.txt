set(SOURCES
		"AdminModule.cpp"
		"keynodes/AdminKeynodes.cpp"
		"agent/GetAdminBuildingRegion.cpp"
		"agent/GetAdminBuildingDistrict.cpp"
		)

set(HEADERS
		"AdminModule.hpp"
		"keynodes/AdminKeynodes.hpp"
		"agent/GetAdminBuildingRegion.hpp"
		"agent/GetAdminBuildingDistrict.hpp"
		)

include_directories(
		${CMAKE_CURRENT_LIST_DIR}
		${SC_MEMORY_SRC}
		${SC_KPM_SRC}
		${SC_TOOLS_SRC}
		${SC_COMMON_MODULE_SRC})

add_library(adminModule SHARED ${SOURCES} ${HEADERS})
target_link_libraries(adminModule sc-memory sc-agents-common)

sc_codegen_ex(adminModule ${CMAKE_CURRENT_LIST_DIR} ${CMAKE_CURRENT_LIST_DIR}/generated)

if(${SC_CLANG_FORMAT_CODE})
	target_clangformat_setup(adminModule)
endif()
