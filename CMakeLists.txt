cmake_minimum_required(VERSION 3.6)
project(jenkinstest LANGUAGES NONE)

set(PYTHON_VERSIONS 3.6.15 3.7.12 3.8.10 3.9.10)
set(NODE_VERSIONS 12 14)

add_custom_target(pyenv_use
    COMMAND printenv | sort
    COMMAND echo -n "before: " && python -V
    COMMAND pyenv local 3.6.15 && python -V
    COMMAND echo -n "after: " && python -V
    COMMAND pyenv local 3.9.10 && python -V
    COMMAND echo -n "again: " && python -V
    WORKING_DIRECTORY ${CMAKE_SOURCE_DIR})

add_custom_target(nvm_use
    COMMAND printenv | grep PATH
    COMMAND echo -n "before: "
    COMMAND export NVM_DIR=/usr/local/nvm && . $NVM_DIR/nvm.sh && nvm use 14
    COMMAND export NVM_DIR=/usr/local/nvm && . $NVM_DIR/nvm.sh && echo -n "after: " && nvm version
    COMMAND export NVM_DIR=/usr/local/nvm && . $NVM_DIR/nvm.sh && nvm use 12
    COMMAND export NVM_DIR=/usr/local/nvm && . $NVM_DIR/nvm.sh && echo -n "again: " && nvm version
    WORKING_DIRECTORY ${CMAKE_SOURCE_DIR})

add_custom_target(pyenv_check ALL DEPENDS pyenv_use
    COMMAND echo -n "second python: " && python -V
    WORKING_DIRECTORY ${CMAKE_SOURCE_DIR})

add_custom_target(nvm_check ALL DEPENDS nvm_use
    COMMAND export NVM_DIR=/usr/local/nvm && . $NVM_DIR/nvm.sh && echo -n "second nvm: " && nvm version
    WORKING_DIRECTORY ${CMAKE_SOURCE_DIR})
