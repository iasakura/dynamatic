set(dhls_src
  src/cmd_parser.cpp
  src/dhls.cpp
  )

set(analyze_src
  src/analyze.cpp
  )

set(elaborate_src
  src/elaborate.cpp
  )

add_executable(dhls ${dhls_src})
add_executable(analyze ${analyze_src})
add_executable(elaborate ${elaborate_src})

target_compile_options(dhls PUBLIC -g -Wall -fpermissive)
