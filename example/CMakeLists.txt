
SET(SRC_FILES
    main.cpp
)

SET(INCLUDE_DIRS
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${OpenCV_INCLUDE_DIRS}
	${CMAKE_CURRENT_SOURCE_DIR}/../include
)

INCLUDE(${QT_USE_FILE})

SET(LIBRARIES
	${OpenCV_LIBS} 
	${QT_LIBRARIES} 
)

# Make sure the compiler can find include files from our library.
INCLUDE_DIRECTORIES(${INCLUDE_DIRS})

# Add binary called "example" that is built from the source file "main.cpp".
# The extension is automatically found.
ADD_EXECUTABLE(example ${SRC_FILES})
TARGET_LINK_LIBRARIES(example find_object ${LIBRARIES})

SET_TARGET_PROPERTIES( example 
  PROPERTIES OUTPUT_NAME ${PROJECT_PREFIX}-example)
  
INSTALL(TARGETS example
        RUNTIME DESTINATION bin COMPONENT runtime
        BUNDLE DESTINATION "${CMAKE_BUNDLE_LOCATION}" COMPONENT runtime)

