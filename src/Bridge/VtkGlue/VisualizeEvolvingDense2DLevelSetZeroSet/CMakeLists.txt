cmake_minimum_required(VERSION 3.16.3)

project( VisualizeEvolvingDense2DLevelSetZeroSet )

find_package( ITK REQUIRED )
include( ${ITK_USE_FILE} )

add_executable( VisualizeEvolvingDense2DLevelSetZeroSet Code.cxx)
target_link_libraries( VisualizeEvolvingDense2DLevelSetZeroSet ${ITK_LIBRARIES} )

install( TARGETS VisualizeEvolvingDense2DLevelSetZeroSet
  DESTINATION bin/ITKSphinxExamples/Bridge/VtkGlue
  COMPONENT Runtime
  )

install( FILES Code.cxx CMakeLists.txt
  DESTINATION share/ITKSphinxExamples/Code/Bridge/VtkGlue/VisualizeEvolvingDense2DLevelSetZeroSet
  COMPONENT Code
  )

enable_testing()
add_test( NAME VisualizeEvolvingDense2DLevelSetZeroSetTest
  COMMAND ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/VisualizeEvolvingDense2DLevelSetZeroSet
    ${CMAKE_CURRENT_BINARY_DIR}/cells.png
    100
  )
set_tests_properties(
  VisualizeEvolvingDense2DLevelSetZeroSetTest
  PROPERTIES LABELS RUNS_LONG
)
