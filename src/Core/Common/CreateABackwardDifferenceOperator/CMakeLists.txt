cmake_minimum_required(VERSION 3.16.3)

project( CreateABackwardDifferenceOperator )

find_package( ITK REQUIRED )
include( ${ITK_USE_FILE} )

add_executable( CreateABackwardDifferenceOperator Code.cxx )
target_link_libraries( CreateABackwardDifferenceOperator ${ITK_LIBRARIES} )

install( TARGETS CreateABackwardDifferenceOperator
  DESTINATION bin/ITKSphinxExamples/Core/Common
  COMPONENT Runtime
)

install( FILES Code.cxx CMakeLists.txt
  DESTINATION share/ITKSphinxExamples/Code/Core/Common/CreateABackwardDifferenceOperator
  COMPONENT Code
)

enable_testing()
add_test( NAME CreateABackwardDifferenceOperatorTest
  COMMAND ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/CreateABackwardDifferenceOperator )
