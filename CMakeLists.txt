cmake_minimum_required(VERSION 3.20)
project(WebSocketServer)

find_package(websocketpp CONFIG REQUIRED)
find_package(OpenSSL REQUIRED)
find_package(Boost COMPONENTS system random REQUIRED)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

add_executable(client client.cpp)
add_executable(server server.cpp)
add_executable(client_chat chat_client.cpp)
add_executable(server_chat chat_server.cpp)

target_link_libraries(client PRIVATE websocketpp::websocketpp ${Boost_LIBRARIES} OpenSSL::SSL OpenSSL::Crypto)
target_link_libraries(server PRIVATE websocketpp::websocketpp ${Boost_LIBRARIES} OpenSSL::SSL OpenSSL::Crypto)
target_link_libraries(client_chat PRIVATE websocketpp::websocketpp ${Boost_LIBRARIES} OpenSSL::SSL OpenSSL::Crypto)
target_link_libraries(server_chat PRIVATE websocketpp::websocketpp ${Boost_LIBRARIES} OpenSSL::SSL OpenSSL::Crypto)
