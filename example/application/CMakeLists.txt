file(GLOB_RECURSE Application_SRC *.cpp *.hpp)

include_directories(
  ${CMAKE_SOURCE_DIR}/src
  ${CMAKE_SOURCE_DIR}/example/dependency
)

add_executable(Application ${Application_SRC})

target_link_libraries(Application
  ${Boost_LIBRARIES}
  HotSwap
  MyDependency
  Singleton
)

if( UNIX )
  install(TARGETS Application DESTINATION bin)
elseif( WIN32 )
  install(TARGETS Application DESTINATION "${CMAKE_INSTALL_PREFIX}")
endif()
