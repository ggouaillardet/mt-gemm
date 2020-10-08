cmake_minimum_required(VERSION 3.16.5)
project (benchmark LANGUAGES C)
 
find_package(OpenMP REQUIRED)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -DUSE_CBLAS")

add_executable(mt-dgemm mt-dgemm.c)
target_link_libraries(mt-dgemm PUBLIC OpenMP::OpenMP_C ${BLAS_LIBS})
install(TARGETS mt-dgemm DESTINATION ${CMAKE_INSTALL_BINDIR} COMPONENT mt-dgemm)

add_executable(mt-sgemm mt-sgemm.c)
target_link_libraries(mt-sgemm PUBLIC OpenMP::OpenMP_C ${BLAS_LIBS})
install(TARGETS mt-sgemm DESTINATION ${CMAKE_INSTALL_BINDIR} COMPONENT mt-sgemm)

