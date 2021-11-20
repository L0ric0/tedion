set(BINARY unit_tests)

add_executable(${BINARY} EXCLUDE_FROM_ALL

)

target_include_directories(${BINARY} PRIVATE include)

target_link_libraries(${BINARY} PRIVATE project_warnings project_options)

target_link_libraries(${BINARY} PRIVATE tedion::tedion)

if (COVERAGE)
        append_coverage_compiler_flags()
        setup_target_for_coverage_gcovr_html(
            NAME ${CMAKE_PROJECT_NAME}_coverage
            EXECUTABLE ctest -j ${PROCESSOR_COUNT}
            DEPENDENCIES ${BINARY}
            EXCLUDE ${PROJECT_SOURCE_DIR}/tests
        )
endif()
