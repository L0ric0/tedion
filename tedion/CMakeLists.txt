add_executable(tedion
    "src/main.cpp"
)

add_executable(tedion::tedion ALIAS tedion)

target_link_libraries(tedion PRIVATE project_options
                                     project_warnings)

target_include_directories(tedion PUBLIC include)
