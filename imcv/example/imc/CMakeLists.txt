#=====================================================
#  _____                _     ____  _____ _   _ _   _ 
# |_   _|_ __ _   _ ___| |_  / __ \|  ___| | | | | | |
#   | | | '__| | | / __| __|/ / _` | |_  | |_| | |_| |
#   | | | |  | |_| \__ \ |_| | (_| |  _| |  _  |  _  |
#   |_| |_|   \__,_|___/\__|\ \__,_|_|   |_| |_|_| |_|
#                            \____/                   
#=====================================================

set(TYPE imc)

MESSAGE( STATUS "" )
MESSAGE( STATUS "-- ${PROJECT_NAME}${TYPE} --" )

# set sourcecode
set(src)
# got with: $ find src \( -iname "*.cpp" -o -iname "*.c" \) -exec echo "set(src \${src} {})" \;
set(src ${src} src/ExampleIMCLibrary.cpp)
set(src ${src} src/ExampleIMC.cpp)

# define shared object
add_library(${PROJECT_NAME}${TYPE} MODULE ${src})

# add libraries
target_link_libraries(${PROJECT_NAME}${TYPE} imunit)

# set version
SET_TARGET_PROPERTIES(${PROJECT_NAME}${TYPE} PROPERTIES VERSION ${TNCFHH_VERSION_MAJOR}.${TNCFHH_VERSION_MINOR}.${TNCFHH_VERSION_PATCH}  SOVERSION 0)

install(TARGETS ${PROJECT_NAME}${TYPE} DESTINATION ${CMAKE_INSTALL_LIBDIR})
