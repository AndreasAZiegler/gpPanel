# -*- mode: cmake; -*-

## add include
include_directories(../include)

############################################################
## sources
file(GLOB cppsrcs "*.cpp" "math/*.cpp" "menu/*.cpp")

## gpPanel library
add_library(gpPanel        SHARED ${cppsrcs})
add_library(gpPanel-static STATIC ${cppsrcs})
# target_link_libraries(gpPanel        ${wxWidgets_LIBRARIES})
# target_link_libraries(gpPanel-static ${wxWidgets_LIBRARIES})

############################################################
## install
install(TARGETS gpPanel  LIBRARY DESTINATION ${INSTALL_LIBDIR}
  PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE
  GROUP_READ GROUP_EXECUTE WORLD_EXECUTE WORLD_READ)
install(TARGETS gpPanel-static  ARCHIVE DESTINATION ${INSTALL_LIBDIR})
