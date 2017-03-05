cmake_minimum_required (VERSION 2.8.6)
project (liblinear)

add_subdirectory(blas)

add_library(tron tron.cpp tron.h)
add_library(linear linear.cpp linear.h)


add_executable (train train.c)
# Link against direct deps (will transitively pull in everything needed).
target_link_libraries(train
        blas
        linear
        tron)

add_executable (predict predict.c)
# Link against direct deps (will transitively pull in everything needed).
target_link_libraries(predict
        blas
        linear
        tron)
