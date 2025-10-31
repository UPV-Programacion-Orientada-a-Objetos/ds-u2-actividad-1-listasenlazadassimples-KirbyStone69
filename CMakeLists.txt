cmake_minimum_required(VERSION 3.10)
project(SensorIoTSystem CXX)

# Habilitar C++11 o superior
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Definir los archivos fuente
set(SOURCE_FILES
    main.cpp
    SensorSystem.cpp
)

# Definir los archivos de cabecera
set(HEADER_FILES
    SensorSystem.h
)

# Definir el nombre del ejecutable y los archivos fuente
add_executable(sensor_manager ${SOURCE_FILES})

# Configuración para documentación con Doxygen
find_package(Doxygen)
if (DOXYGEN_FOUND)
    # Configurar archivo Doxyfile
    set(DOXYGEN_PROJECT_NAME "Sistema IoT de Monitoreo Polimórfico")
    set(DOXYGEN_PROJECT_BRIEF "Sistema de gestión de sensores usando polimorfismo y templates")
    set(DOXYGEN_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/doxygen_docs)
    set(DOXYGEN_EXTRACT_ALL YES)
    set(DOXYGEN_EXTRACT_PRIVATE YES)
    set(DOXYGEN_EXTRACT_STATIC YES)
    set(DOXYGEN_GENERATE_HTML YES)
    
    # Generar documentación
    doxygen_add_docs(doc 
        ${SOURCE_FILES} 
        ${HEADER_FILES}
        COMMENT "Generando documentación con Doxygen"
    )
endif()