# Find sources.
file(GLOB metis_sources *.c)
# Build libmetis.
add_library(metis ${METIS_LIBRARY_TYPE} ${GKlib_sources} ${metis_sources})
target_link_options(metis PRIVATE /DEF:src/libmetis/CMakeFiles/metis.dir/./exports.def)
target_include_directories(metis PUBLIC
$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
$<INSTALL_INTERFACE:include>
PRIVATE ${PROJECT_SOURCE_DIR}/src/GKlib ${PROJECT_BINARY_DIR}/src/include
)
target_link_libraries(metis PRIVATE $<$<BOOL:${UNIX}>:m>)

install(TARGETS metis)
