cmake_minimum_required(VERSION 3.10)

project(dynamatic CXX)

add_subdirectory(elastic-circuits)
add_subdirectory(Buffers)
add_subdirectory(dot2vhdl)
add_subdirectory(Frontend)

set(PERM755 OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE)
set(PERM655 OWNER_READ OWNER_WRITE GROUP_READ WORLD_READ)

install(TARGETS
  ElasticPass
  LLVMMemElemInfo
  LLVMOptimizeBitWidth
  MyCFGPass
  FrequencyCounterPass
  FrequencyDataGatherPass
  PERMISSIONS ${PERM}
  DESTINATION llvm_passes)

install(TARGETS
  dhls
  analyze
  elaborate
  buffers
  dot2vhdl
  PERMISSIONS ${PERM}
  DESTINATION bin)

install(FILES
  ${PROJECT_SOURCE_DIR}/bin/compile
  ${PROJECT_SOURCE_DIR}/bin/create_project
  ${PROJECT_SOURCE_DIR}/bin/dcfg
  ${PROJECT_SOURCE_DIR}/bin/design_compiler
  ${PROJECT_SOURCE_DIR}/bin/dynamatic
  ${PROJECT_SOURCE_DIR}/bin/lsq_generate
  ${PROJECT_SOURCE_DIR}/bin/update-dynamatic
  ${PROJECT_SOURCE_DIR}/bin/write_hdl
  PERMISSIONS ${PERM755}
  DESTINATION bin)

# TODO: Fix the pass
install(FILES
  ${PROJECT_SOURCE_DIR}/elastic-circuits/FrequencyCounterPass/log_FrequencyCounter.c
  PERMISSIONS ${PERM644}
  DESTINATION llvm_passes)

install(FILES
  ${PROJECT_SOURCE_DIR}/chisel_lsq/jar/lsq.jar
  PERMISSIONS ${PERM644}
  DESTINATION jar)

install(FILES
  ${PROJECT_SOURCE_DIR}/components/MemCont.vhd
  ${PROJECT_SOURCE_DIR}/components/arithmetic_units.vhd
  ${PROJECT_SOURCE_DIR}/components/delay_buffer.vhd
  ${PROJECT_SOURCE_DIR}/components/elastic_components.vhd
  ${PROJECT_SOURCE_DIR}/components/mul_wrapper.vhd
  ${PROJECT_SOURCE_DIR}/components/multipliers.vhd
  PERMISSIONS ${PERM644}
  DESTINATION components)
