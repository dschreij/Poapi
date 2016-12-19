cmake_minimum_required (VERSION 3.1.0)
project (POAPI)

include_directories(OAPI/ndlib/include)
set(OAPI_LIB
	OAPI/ndlib/msvc/oapi.lib
)
set(POAPI_SRC
	../poapi.c
)

add_executable(POAPI
	${POAPI_SRC}
)
target_link_libraries(POAPI
	${OAPI_LIB}
)
set_target_properties(POAPI
	PROPERTIES PREFIX "" OUTPUT_NAME "poapi"
)