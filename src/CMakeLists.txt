set(Boost_USE_STATIC_LIBS OFF) 
set(Boost_USE_MULTITHREADED ON)  
set(Boost_USE_STATIC_RUNTIME OFF) 
find_package(Boost REQUIRED COMPONENTS system)
INCLUDE_DIRECTORIES( ${Boost_INCLUDE_DIR} )

install(FILES
    SnetConfig.h
    SnetAppMessage.h
    SnetPacket.h
    SnetServiceMessage.h
DESTINATION include)
