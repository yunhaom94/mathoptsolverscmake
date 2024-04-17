# Enable ExternalProject.
include(ExternalProject)

# COIN-OR CLP/CBC

add_library(MathOptSolversCMake_osi INTERFACE)
if(UNIX AND NOT APPLE)
    ExternalProject_Add(Osi
        URL https://github.com/coin-or/Osi/releases/download/releases%2F0.108.8/Osi-releases.0.108.8-x86_64-ubuntu20-gcc940-static.tar.gz
        URL_HASH SHA256=bd5a5bf1e6b6a28d13d41ab1554becd9f3992afe775785e51a88c9405cf2853e
        CONFIGURE_COMMAND ""
        BUILD_COMMAND ""
        INSTALL_COMMAND ""
        TEST_COMMAND "")
    target_include_directories(MathOptSolversCMake_osi INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/Osi-prefix/src/Osi/include")
    target_link_directories(MathOptSolversCMake_osi INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/Osi-prefix/src/Osi/lib")
    target_link_libraries(MathOptSolversCMake_osi INTERFACE
        libOsi.a
        libOsiCommonTests.a)
endif()
if(APPLE)
    ExternalProject_Add(Osi
        URL https://github.com/coin-or/Osi/releases/download/releases%2F0.108.8/Osi-releases.0.108.8-x86_64-macos106-clang140.tar.gz
        URL_HASH SHA256=4ddc1ee5cd5088aeb7795bfebc66beec8d7a0a3baec3dd3e8bbbdff17f93cd3f
        CONFIGURE_COMMAND ""
        BUILD_COMMAND ""
        INSTALL_COMMAND ""
        TEST_COMMAND "")
    target_include_directories(MathOptSolversCMake_osi INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/Osi-prefix/src/Osi/include")
    target_link_directories(MathOptSolversCMake_osi INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/Osi-prefix/src/Osi/lib")
    target_link_libraries(MathOptSolversCMake_osi INTERFACE
        libOsi.dylib
        libOsiCommonTests.dylib)
    install(FILES "${CMAKE_CURRENT_BINARY_DIR}/Osi-prefix/src/Osi/lib/libOsi.dylib" DESTINATION lib)
    install(FILES "${CMAKE_CURRENT_BINARY_DIR}/Osi-prefix/src/Osi/lib/libOsiCommonTests.dylib" DESTINATION lib)
endif()
if(WIN32)
    ExternalProject_Add(Osi
        URL https://github.com/coin-or/Osi/releases/download/releases%2F0.108.8/Osi-releases.0.108.8-w64-msvc16-md.zip
        URL_HASH SHA256=a61fc462cb598139d205cd2323522581a01900575d0d6bccf660b6c7e1b0b71c
        CONFIGURE_COMMAND ""
        BUILD_COMMAND ""
        INSTALL_COMMAND ""
        TEST_COMMAND "")
    target_include_directories(MathOptSolversCMake_osi INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/Osi-prefix/src/Osi/include")
    target_compile_option(MathOptSolversCMake_osi INTERFACE
        /MT)
    target_link_directories(MathOptSolversCMake_osi INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/Osi-prefix/src/Osi/lib")
    target_link_libraries(MathOptSolversCMake_osi INTERFACE
        libOsi.lib
        libOsiCommonTests.lib)
endif()
add_library(MathOptSolversCMake::osi ALIAS MathOptSolversCMake_osi)

add_library(MathOptSolversCMake_coinutils INTERFACE)
if(UNIX AND NOT APPLE)
    ExternalProject_Add(CoinUtils
        URL https://github.com/coin-or/CoinUtils/releases/download/releases%2F2.11.9/CoinUtils-releases.2.11.9-x86_64-ubuntu20-gcc940-static.tar.gz
        URL_HASH SHA256=14d07de1b7961f68e037da6f0c57844fd67d4cc1a4b125642f42cd134b228094
        CONFIGURE_COMMAND ""
        BUILD_COMMAND ""
        INSTALL_COMMAND ""
        TEST_COMMAND "")
    target_include_directories(MathOptSolversCMake_coinutils INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/CoinUtils-prefix/src/CoinUtils/include")
    target_link_directories(MathOptSolversCMake_coinutils INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/CoinUtils-prefix/src/CoinUtils/lib")
    target_link_libraries(MathOptSolversCMake_coinutils INTERFACE
        libCoinUtils.a
        liblapack.a
        libblas.a
        libbz2.a
        libz.a
        libgfortran.a
        libquadmath.a)
endif()
if(APPLE)
    ExternalProject_Add(CoinUtils
        URL https://github.com/coin-or/CoinUtils/releases/download/releases%2F2.11.9/CoinUtils-releases.2.11.9-x86_64-macos106-clang140.tar.gz
        URL_HASH SHA256=3d0bdaf7bb748bfbec059fc8ff6ff17d2354c334710db3cd532af6a9c942f762
        CONFIGURE_COMMAND ""
        BUILD_COMMAND ""
        INSTALL_COMMAND ""
        TEST_COMMAND "")
    target_include_directories(MathOptSolversCMake_coinutils INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/CoinUtils-prefix/src/CoinUtils/include")
    target_link_directories(MathOptSolversCMake_coinutils INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/CoinUtils-prefix/src/CoinUtils/lib")
    target_link_libraries(MathOptSolversCMake_coinutils INTERFACE
        libCoinUtils.dylib)
    install(FILES "${CMAKE_CURRENT_BINARY_DIR}/CoinUtils-prefix/src/CoinUtils/lib/libCoinUtils.dylib" DESTINATION lib)
endif()
if(WIN32)
    ExternalProject_Add(CoinUtils
        URL https://github.com/coin-or/CoinUtils/releases/download/releases%2F2.11.9/CoinUtils-releases.2.11.9-w64-msvc16-md.zip
        URL_HASH SHA256=2bc64f0afd80113571697e949b2663e9047272decf90d5f62e452c2628d33ca6
        CONFIGURE_COMMAND ""
        BUILD_COMMAND ""
        INSTALL_COMMAND ""
        TEST_COMMAND "")
    target_include_directories(MathOptSolversCMake_coinutils INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/CoinUtils-prefix/src/CoinUtils/include")
    target_compile_options(MathOptSolversCMake_coinutils INTERFACE
        /MT)
    target_link_directories(MathOptSolversCMake_coinutils INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/CoinUtils-prefix/src/CoinUtils/lib")
    target_link_libraries(MathOptSolversCMake_coinutils INTERFACE
        libCoinUtils.lib)
endif()
add_library(MathOptSolversCMake::coinutils ALIAS MathOptSolversCMake_coinutils)

add_library(MathOptSolversCMake_clp INTERFACE)
if(UNIX AND NOT APPLE)
    ExternalProject_Add(Clp
        URL https://github.com/coin-or/Clp/releases/download/releases%2F1.17.8/Clp-releases.1.17.8-x86_64-ubuntu20-gcc940-static.tar.gz
        URL_HASH SHA256=d569b04d19c25876e55d2557a1d9739df8eb50ec8ca11a98ad387fd8b90212c9
        CONFIGURE_COMMAND ""
        BUILD_COMMAND ""
        INSTALL_COMMAND ""
        TEST_COMMAND "")
    target_include_directories(MathOptSolversCMake_clp INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/Clp-prefix/src/Clp/include")
    target_link_directories(MathOptSolversCMake_clp INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/Clp-prefix/src/Clp/lib")
    target_link_libraries(MathOptSolversCMake_clp INTERFACE
        libClp.a
        libOsiClp.a)
endif()
if(APPLE)
    ExternalProject_Add(Clp
        URL https://github.com/coin-or/Clp/releases/download/releases%2F1.17.8/Clp-releases.1.17.8-x86_64-macos106-clang140.tar.gz
        URL_HASH SHA256=fe9ce251cd3e0324d64f0e3956d722c73b7568685c25eb7559c327818b39b86b
        CONFIGURE_COMMAND ""
        BUILD_COMMAND ""
        INSTALL_COMMAND ""
        TEST_COMMAND "")
    target_include_directories(MathOptSolversCMake_clp INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/Clp-prefix/src/Clp/include")
    target_link_directories(MathOptSolversCMake_clp INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/Clp-prefix/src/Clp/lib")
    target_link_libraries(MathOptSolversCMake_clp INTERFACE
        libClp.dylib
        libOsiClp.dylib)
    install(FILES "${CMAKE_CURRENT_BINARY_DIR}/Clp-prefix/src/Clp/lib/libClp.dylib" DESTINATION lib)
    install(FILES "${CMAKE_CURRENT_BINARY_DIR}/Clp-prefix/src/Clp/lib/libOsiClp.dylib" DESTINATION lib)
endif()
if(WIN32)
    ExternalProject_Add(Clp
        URL https://github.com/coin-or/Clp/releases/download/releases%2F1.17.8/Clp-releases.1.17.8-w64-msvc16-md.zip
        URL_HASH SHA256=e37c834aea5c31dfd8620b7d2432cb31fc16ecb0c6ffb398e8f07c9c82dd5028
        CONFIGURE_COMMAND ""
        BUILD_COMMAND ""
        INSTALL_COMMAND ""
        TEST_COMMAND "")
    target_include_directories(MathOptSolversCMake_clp INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/Clp-prefix/src/Clp/include")
    target_link_directories(MathOptSolversCMake_clp INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/Clp-prefix/src/Clp/lib")
    target_link_libraries(MathOptSolversCMake_clp INTERFACE
        libClp.lib
        libOsiClp.lib)
endif()
target_link_libraries(MathOptSolversCMake_clp INTERFACE
    MathOptSolversCMake_osi
    MathOptSolversCMake_coinutils)
add_library(MathOptSolversCMake::clp ALIAS MathOptSolversCMake_clp)

add_library(MathOptSolversCMake_cbc INTERFACE)
if(UNIX AND NOT APPLE)
    ExternalProject_Add(Cbc
        URL https://github.com/coin-or/Cbc/releases/download/releases%2F2.10.10/Cbc-releases.2.10.10-x86_64-ubuntu20-gcc940-static.tar.gz
        URL_HASH SHA256=872c78bfcdd1566f134d2f7757b76b2a2479a5b1ade065cdd1d4b303ed6f8006
        CONFIGURE_COMMAND ""
        BUILD_COMMAND ""
        INSTALL_COMMAND ""
        TEST_COMMAND "")
    target_include_directories(MathOptSolversCMake_cbc INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/Cbc-prefix/src/Cbc/include")
    target_link_directories(MathOptSolversCMake_cbc INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/Cbc-prefix/src/Cbc/lib")
    target_link_libraries(MathOptSolversCMake_cbc INTERFACE
        libCbc.a
        libOsiCbc.a
        libCgl.a)
endif()
if(APPLE)
    ExternalProject_Add(Cbc
        URL https://github.com/coin-or/Cbc/releases/download/releases%2F2.10.10/Cbc-releases.2.10.10-x86_64-macos106-clang140.tar.gz
        URL_HASH SHA256=2b864f174ceabad2c6f2096180d737d36d33e7a0553211265557af187329cb94
        CONFIGURE_COMMAND ""
        BUILD_COMMAND ""
        INSTALL_COMMAND ""
        TEST_COMMAND "")
    target_include_directories(MathOptSolversCMake_cbc INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/Cbc-prefix/src/Cbc/include")
    target_link_directories(MathOptSolversCMake_cbc INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/Cbc-prefix/src/Cbc/lib")
    target_link_libraries(MathOptSolversCMake_cbc INTERFACE
        libCbc.dylib
        libOsiCbc.dylib
        libCgl.dylib)
    install(FILES "${CMAKE_CURRENT_BINARY_DIR}/Cbc-prefix/src/Cbc/lib/libCbc.dylib" DESTINATION lib)
    install(FILES "${CMAKE_CURRENT_BINARY_DIR}/Cbc-prefix/src/Cbc/lib/libOsiCbc.dylib" DESTINATION lib)
    install(FILES "${CMAKE_CURRENT_BINARY_DIR}/Cbc-prefix/src/Cbc/lib/libCgl.dylib" DESTINATION lib)
endif()
if(WIN32)
    ExternalProject_Add(Cbc
        URL https://github.com/coin-or/Cbc/releases/download/releases%2F2.10.10/Cbc-releases.2.10.10-w64-msvc16-md.zip
        URL_HASH SHA256=94a951904eb80c2f351785fc9340216e88970a716634bc1ccd8b4fc5024af37c
        CONFIGURE_COMMAND ""
        BUILD_COMMAND ""
        INSTALL_COMMAND ""
        TEST_COMMAND "")
    target_include_directories(MathOptSolversCMake_cbc INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/Cbc-prefix/src/Cbc/include")
    target_link_directories(MathOptSolversCMake_cbc INTERFACE
        "${CMAKE_CURRENT_BINARY_DIR}/Cbc-prefix/src/Cbc/lib")
    target_link_libraries(MathOptSolversCMake_cbc INTERFACE
        libCbc.lib
        libOsiCbc.lib
        libCgl.lib)
endif()
target_link_libraries(MathOptSolversCMake_cbc INTERFACE
    MathOptSolversCMake_clp)
add_library(MathOptSolversCMake::cbc ALIAS MathOptSolversCMake_cbc)
