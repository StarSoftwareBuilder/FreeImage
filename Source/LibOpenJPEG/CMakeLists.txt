cmake_minimum_required(VERSION 2.6.1)

add_definitions(-DOPJ_STATIC -D_CRT_SECURE_NO_DEPRECATE)

set( LIBOPENJPEG_SOURCES 
    bio.c cio.c dwt.c event.c 
    function_list.c
    image.c invert.c
    j2k.c jp2.c 
    mct.c mqc.c openjpeg.c 
    opj_clock.c pi.c 
    raw.c t1.c t1_generate_luts.c t2.c 
    tcd.c tgt.c bio.h cio.h dwt.h event.h 
    function_list.h
    image.h indexbox_manager.h
    invert.h
    j2k.h jp2.h 
    mct.h mqc.h openjpeg.h opj_config.h opj_config_private.h
    opj_clock.h
    opj_includes.h 
    opj_intmath.h
    opj_inttypes.h
    opj_malloc.h opj_stdint.h 
    pi.h raw.h t1.h t1_luts.h 
    t2.h tcd.h tgt.h 
)

#add_definitions(-DPNG_BUILD_DLL)
if(CMAKE_SYSTEM_PROCESSOR MATCHES "x86_64") 
  add_definitions(-fPIC) 
endif()

add_library ( LibOpenJPEG_s STATIC ${LIBOPENJPEG_SOURCES} )

  if(FREEIMAGE_BUILD_STATIC)
    INSTALL(TARGETS 
    LibOpenJPEG_s
    RUNTIME DESTINATION "${CMAKE_INSTALL_PREFIX}/bin" 
    ARCHIVE DESTINATION "${CMAKE_INSTALL_PREFIX}/lib" 
    LIBRARY DESTINATION "${CMAKE_INSTALL_PREFIX}/lib"
    )
  endif()  
