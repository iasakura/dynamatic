set(dot2vhdl_src
  src/table_printer.cpp
  src/dot_parser.cpp
  src/vhdl_writer.cpp
  src/lsq_generator.cpp
  src/checks.cpp
  src/eda_if.cpp
  src/reports.cpp
  src/string_utils.cpp
  src/sys_utils.cpp
  src/dot2vhdl.cpp
  )

add_executable(dot2vhdl ${dot2vhdl_src})

target_compile_options(dot2vhdl PUBLIC -O3 -g -Wall -static -fpermissive)
