set(SRC_PATH ${PROJECT_SOURCE_DIR}/src)
set(INCLUDE_PATH ${PROJECT_SOURCE_DIR}/includes)

set(INCLUDE_DIRS
     ${INCLUDE_PATH}/raudio/
     ${INCLUDE_PATH}/rcore/
     ${INCLUDE_PATH}/rcore/input/
     ${INCLUDE_PATH}/rmodels/
     ${INCLUDE_PATH}/rshapes/
     ${INCLUDE_PATH}/rtext/
     ${INCLUDE_PATH}/rtextures/
)

set(SOURCES
    ${SRC_PATH}/raudio/audio.cpp
    ${SRC_PATH}/raudio/audioStream.cpp
    ${SRC_PATH}/raudio/music.cpp
    ${SRC_PATH}/raudio/sound.cpp
    ${SRC_PATH}/raudio/wave.cpp

    ${SRC_PATH}/rcore/input/gamepad.cpp
    ${SRC_PATH}/rcore/input/keyboard.cpp
    ${SRC_PATH}/rcore/input/mouse.cpp
    ${SRC_PATH}/rcore/input/touch.cpp
    ${SRC_PATH}/rcore/callback.cpp
    ${SRC_PATH}/rcore/camera.cpp
    ${SRC_PATH}/rcore/compress.cpp
    ${SRC_PATH}/rcore/cursor.cpp
    ${SRC_PATH}/rcore/drawing.cpp
    ${SRC_PATH}/rcore/file.cpp
    ${SRC_PATH}/rcore/gesture.cpp
    ${SRC_PATH}/rcore/misc.cpp
    ${SRC_PATH}/rcore/screenSpace.cpp
    ${SRC_PATH}/rcore/shader.cpp
    ${SRC_PATH}/rcore/timing.cpp
    ${SRC_PATH}/rcore/vr.cpp
    ${SRC_PATH}/rcore/window.cpp

    ${SRC_PATH}/rmodels/animation.cpp
    ${SRC_PATH}/rmodels/basic.cpp
    ${SRC_PATH}/rmodels/collision.cpp
    ${SRC_PATH}/rmodels/draw.cpp
    ${SRC_PATH}/rmodels/load.cpp
    ${SRC_PATH}/rmodels/material.cpp
    ${SRC_PATH}/rmodels/mesh.cpp

    ${SRC_PATH}/rshapes/collision.cpp
    ${SRC_PATH}/rshapes/draw.cpp

    ${SRC_PATH}/rtext/codepoint.cpp
    ${SRC_PATH}/rtext/font.cpp
    ${SRC_PATH}/rtext/text.cpp

    ${SRC_PATH}/rtextures/color.cpp
    ${SRC_PATH}/rtextures/generation.cpp
    ${SRC_PATH}/rtextures/imageDraw.cpp
    ${SRC_PATH}/rtextures/imageManip.cpp
    ${SRC_PATH}/rtextures/load.cpp
    ${SRC_PATH}/rtextures/texture.cpp
)

set(HEADERS
    ${INCLUDE_PATH}/raudio/audio.hpp
    ${INCLUDE_PATH}/raudio/audioStream.hpp
    ${INCLUDE_PATH}/raudio/music.hpp
    ${INCLUDE_PATH}/raudio/sound.hpp
    ${INCLUDE_PATH}/raudio/wave.hpp

    ${INCLUDE_PATH}/rcore/input/gamepad.hpp
    ${INCLUDE_PATH}/rcore/input/keyboard.hpp
    ${INCLUDE_PATH}/rcore/input/mouse.hpp
    ${INCLUDE_PATH}/rcore/input/touch.hpp
    ${INCLUDE_PATH}/rcore/callback.hpp
    ${INCLUDE_PATH}/rcore/camera.hpp
    ${INCLUDE_PATH}/rcore/compress.hpp
    ${INCLUDE_PATH}/rcore/cursor.hpp
    ${INCLUDE_PATH}/rcore/drawing.hpp
    ${INCLUDE_PATH}/rcore/file.hpp
    ${INCLUDE_PATH}/rcore/gesture.hpp
    ${INCLUDE_PATH}/rcore/misc.hpp
    ${INCLUDE_PATH}/rcore/screenSpace.hpp
    ${INCLUDE_PATH}/rcore/shader.hpp
    ${INCLUDE_PATH}/rcore/timing.hpp
    ${INCLUDE_PATH}/rcore/vr.hpp
    ${INCLUDE_PATH}/rcore/window.hpp

    ${INCLUDE_PATH}/rmodels/animation.hpp
    ${INCLUDE_PATH}/rmodels/basic.hpp
    ${INCLUDE_PATH}/rmodels/modelsCollision.hpp
    ${INCLUDE_PATH}/rmodels/modelsDraw.hpp
    ${INCLUDE_PATH}/rmodels/load.hpp
    ${INCLUDE_PATH}/rmodels/material.hpp
    ${INCLUDE_PATH}/rmodels/mesh.hpp

    ${INCLUDE_PATH}/rshapes/shapesCollision.hpp
    ${INCLUDE_PATH}/rshapes/shapesDraw.hpp

    ${INCLUDE_PATH}/rtext/codepoint.hpp
    ${INCLUDE_PATH}/rtext/font.hpp
    ${INCLUDE_PATH}/rtext/text.hpp

    ${INCLUDE_PATH}/rtextures/color.hpp
    ${INCLUDE_PATH}/rtextures/generation.hpp
    ${INCLUDE_PATH}/rtextures/imageDraw.hpp
    ${INCLUDE_PATH}/rtextures/imageManip.hpp
    ${INCLUDE_PATH}/rtextures/load.hpp
    ${INCLUDE_PATH}/rtextures/texture.hpp
)

add_library(${PROJECT_NAME} SHARED
    ${SOURCES}
    ${HEADERS}    
)

target_include_directories(${PROJECT_NAME} PRIVATE ${INCLUDE_DIRS})
set_target_properties(${PROJECT_NAME} PROPERTIES VERSION ${PROJECT_VERSION})
set_target_properties(${PROJECT_NAME} PROPERTIES SOVERSION ${PROJECT_VERSION_MAJOR})
set_target_properties(${PROJECT_NAME} PROPERTIES PUBLIC_HEADER "${HEADERS}")

include(GNUInstallDirs)
install(TARGETS ${PROJECT_NAME}
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
)