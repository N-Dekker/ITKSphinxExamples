cmake_minimum_required(VERSION 3.16.3)

project( CovariantVectorNorm )

find_package( ITK REQUIRED )
include( ${ITK_USE_FILE} )

add_executable( CovariantVectorNorm Code.cxx )
target_link_libraries( CovariantVectorNorm ${ITK_LIBRARIES} )

install( TARGETS CovariantVectorNorm
  DESTINATION bin/ITKSphinxExamples/Core/Common
  COMPONENT Runtime
)

install( FILES Code.cxx CMakeLists.txt
  DESTINATION share/ITKSphinxExamples/Code/Core/Common/CovariantVectorNorm
  COMPONENT Code
)

enable_testing()
add_test( NAME CovariantVectorNormTest
  COMMAND ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/CovariantVectorNorm )
