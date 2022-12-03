SET(libSlice3rBase slice3rBase)
project(libSlice3rBase )
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

if(WIN32)
    SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /bigobj")
endif()

find_package(Eigen3 CONFIG REQUIRED)
add_subdirectory(clipper)

set(SRCS	Int128.hpp
			libslic3r.h
			Point.cpp
			Point.hpp
			Polygon.cpp
			Polygon.hpp
			Polyline.cpp
			Polyline.hpp
			Line.cpp
			Line.hpp
			LocalesUtils.cpp
			LocalesUtils.hpp
			MultiPoint.cpp
			MultiPoint.hpp
			BoundingBox.cpp
			BoundingBox.hpp
			Geometry.cpp
			Geometry.hpp
			ExPolygon.cpp
			ExPolygon.hpp
			clipper.cpp
			clipper.hpp
			ClipperUtils.cpp
			ClipperUtils.hpp
			Surface.cpp
			Surface.hpp
			
			fast_float/fast_float.h
			
			
			Circle.hpp
			Circle.cpp
			ArcFitter.hpp
			ArcFitter.cpp
			)

add_library(${libSlice3rBase} STATIC ${SRCS})

target_link_libraries(${libSlice3rBase}  Eigen3::Eigen clipper)
