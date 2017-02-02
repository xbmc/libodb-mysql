cmake_minimum_required(VERSION 3.2)

project(libodb-mysql VERSION 2.4.0 LANGUAGES CXX)

if(MSVC)
  set(CMAKE_DEBUG_POSTFIX d)
endif()

find_package(libodb REQUIRED NO_MODULE)
find_package(libmysql REQUIRED NO_MODULE)

add_library(libodb-mysql
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/connection.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/connection.ixx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/connection-factory.cxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/connection-factory.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/container-statements.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/container-statements.txx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/database.cxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/database.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/database.ixx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/enum.cxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/enum.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/error.cxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/error.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/exceptions.cxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/exceptions.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/forward.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/mysql.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/mysql-types.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/no-id-object-result.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/no-id-object-result.txx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/no-id-object-statements.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/no-id-object-statements.txx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/polymorphic-object-result.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/polymorphic-object-result.txx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/polymorphic-object-statements.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/polymorphic-object-statements.txx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/prepared-query.cxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/prepared-query.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/query.cxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/query.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/query.ixx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/query.txx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/query-const-expr.cxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/query-dynamic.cxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/query-dynamic.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/query-dynamic.ixx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/query-dynamic.txx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/section-statements.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/section-statements.txx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/simple-object-result.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/simple-object-result.txx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/simple-object-statements.cxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/simple-object-statements.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/simple-object-statements.ixx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/simple-object-statements.txx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/statement.cxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/statement.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/statement-cache.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/statement-cache.txx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/statements-base.cxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/statements-base.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/tracer.cxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/tracer.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/traits.cxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/traits.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/traits-calls.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/transaction.cxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/transaction.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/transaction.ixx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/transaction-impl.cxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/transaction-impl.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/transaction-impl.ixx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/version.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/view-result.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/view-result.txx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/view-statements.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/view-statements.txx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/auto-handle.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/binding.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/config.h.in
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/connection.cxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/details/export.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/details/options.cli
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/details/options.cxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/details/options.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/details/options.ixx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/details/config.hxx
${CMAKE_CURRENT_SOURCE_DIR}/odb/mysql/details/conversion.hxx
)

target_include_directories(libodb-mysql
  PRIVATE
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
  INTERFACE
  $<INSTALL_INTERFACE:include/odb>
  PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/odb>
)

target_compile_definitions(libodb-mysql
  PRIVATE
  _CRT_SECURE_NO_WARNINGS
  _CRT_STDC_NO_DEPRECATE
  _USRDLL
  LIBODB_MYSQL_DYNAMIC_LIB
)

target_link_libraries(libodb-mysql
  PRIVATE
  libodb::libodb
  libmysql::libmysql
)

include(CMakePackageConfigHelpers)
write_basic_package_version_file(
  ${CMAKE_CURRENT_BINARY_DIR}/${PROJECT_NAME}-config-version.cmake
  VERSION ${PROJECT_VERSION}
  COMPATIBILITY AnyNewerVersion
)

install(TARGETS libodb-mysql EXPORT libodb-mysql
  RUNTIME DESTINATION bin
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
)

install(DIRECTORY
  ${CMAKE_CURRENT_SOURCE_DIR}/odb
  DESTINATION include
  PATTERN *.cxx EXCLUDE
)

install(EXPORT libodb-mysql
  FILE
  ${PROJECT_NAME}.cmake
  NAMESPACE
    ${PROJECT_NAME}::
  DESTINATION
    lib/cmake/${PROJECT_NAME}
)

install(FILES
  cmake/${PROJECT_NAME}-config.cmake
  ${CMAKE_CURRENT_BINARY_DIR}/${PROJECT_NAME}-config-version.cmake
  DESTINATION
    lib/cmake/${PROJECT_NAME}
)

export(TARGETS libodb-mysql
  FILE
  ${CMAKE_CURRENT_BINARY_DIR}/${PROJECT_NAME}-config.cmake
  NAMESPACE ${PROJECT_NAME}::
)