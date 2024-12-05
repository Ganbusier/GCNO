cmake_minimum_required(VERSION 3.17)

find_package(GMP REQUIRED)

if (GMP_FOUND)
    message(STATUS "GMP found: ${GMP_LIBRARIES}")
    message(STATUS "GMP include dir: ${GMP_INCLUDE_DIR}")
else ()
    message(FATAL_ERROR "GMP not found")
endif ()

find_package(OpenMP REQUIRED)

add_executable(MAIN main.cpp)
target_link_libraries(MAIN 
						Algorithm 
						BaseShape 
						Draw 
						Geodesic 
						Integral 
						Model 
						Optimization 
						PointCloudProcessing 
						PQP 
						Reconstruction 
						Tessellation2D 
						Tessellation3D 
						CVTLike
						${GMP_LIBRARIES}
						OpenMP::OpenMP_CXX)
target_include_directories(MAIN PUBLIC
	$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/include>
	$<INSTALL_INTERFACE:include>)