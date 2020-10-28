find_package(PkgConfig)

pkg_check_modules(LIBGVC REQUIRED libgvc)

set(buffers_src
  src/test.cpp
  src/Dataflow.cpp
  src/DFnetlist.cpp
  src/DFlib.cpp
  src/DFnetlsit_BasicBlocks.cpp
  src/DFnetlist_BBcycles.cpp
  src/DFnetlist_buffers.cpp
  src/DFnetlist_channel_width.cpp
  src/DFnetlist_check.cpp 
  src/DFnetlist_Connectivity.cpp
  src/DFnetlist_MG.cpp
  src/DFnetlist_Optimize.cpp
  src/DFnetlist_read_dot.cpp
  src/DFnetlist_write_dot.cpp)

add_executable(buffers
  ${buffers_src}
  )

target_include_directories(buffers PRIVATE ${LIBGVC_INCLUDE_DIRS})
target_link_libraries(buffers ${LIBGVC_LIBRARIES})
