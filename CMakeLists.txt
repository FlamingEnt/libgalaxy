cmake_minimum_required(VERSION 3.2...3.5)

project(libgalaxy VERSION 5.00b LANGUAGES C ASM_MASM)

string(APPEND CMAKE_ASM_MASM_FLAGS " /Cp /Cx")

file(GLOB HEADERS *.h Hdr/*.h)
source_group("Header Files" FILES ${HEADERS})

file(GLOB SOURCES *.c *.asm)
source_group("Source Files" FILES ${SOURCES})

# Excluded Items
list(REMOVE_ITEM SOURCES
	${CMAKE_CURRENT_SOURCE_DIR}/Sbs.asm
	${CMAKE_CURRENT_SOURCE_DIR}/eax.c
	${CMAKE_CURRENT_SOURCE_DIR}/huffdec.c
)

add_library(libgalaxy STATIC ${HEADERS} ${SOURCES})

target_include_directories(libgalaxy PRIVATE Hdr)