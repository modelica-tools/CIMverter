# CIMverter
This tool is used to convert CIM-XML-RDF files into Modelica code.

## Licensing
For **non-commercial** use this software is licensed under the terms in the included [LICENSE](LICENSE) file.
In case of **commercial** use you are required to negotiate a proper license model with the *Institute for Automation of Complex Power Systems* at *RWTH Aachen University*. Therefor please write to [acs-sek@eonerc.rwth-aachen.de](mailto:acs-sek@eonerc.rwth-aachen.de).

## Dependencies:
* cmake >=3.5
* clang
* Boost >= 1.60.0
* ctemplate >= 2.3
* libconifg++
* as submodule: libcimpp with arabica
* (Doxygen)

## Installation steps for Ubuntu Linux:

### Install cmake:

    sudo apt-get install cmake

### Install clang:

    sudo apt-get install clang

### Get the required libraries:

    sudo apt-get update
    sudo apt-get install build-essential g++ python-dev autotools-dev libicu-dev build-essential libbz2-dev libboost-all-dev

### Install ctemplate:

    sudo apt-get install libctemplate-dev

### Install Doxygen

    sudo apt-get install doxygen

### Install Graphviz for document Graph generation

    sudo apt-get install graphviz

### Install libconfig++

    sudo apt-get install libconfig++-dev


### To build the CIMverter using cmake by following steps:

#### Get submodules and GridData submodule:

    git submodule update --init --recursive --remote

#### Build CIMverter with all submodules

##### 1. Create build directory

    mkdir build

##### 2. Change into build directory and run cmake

    cd build/
    cmake -DCMAKE_BUILD_TYPE=Release ..

##### 3. Compile CIMverter and CIMParser

    make -j4

##### 4. [optional] Generate doxygen documentation

    make document

#### Usage:

    cd build/bin
    

##### Command for Usage help:

    ./CIMverter --help

***

***
## For developers:

### How to update the lastest submodule:

    1. cd submodule directory
    2. git checkout master or git checkout release
    3. git pull
    4. git submodule update

### Buid in debug mode:

    cd build/
    cmake -DCMAKE_BUILD_TYPE=Debug ..

### Recommand using clion IDE with cmake build system:

* Makefile will not be used any more because arabica xml parser

### Project Folder may has authority problem on Linux:

    sudo chown -R [your account username] CIMverter/
    
### setDependencyCheckOff() should be added right now before bug fixed of the CIM Parser
    see line 133 in main.cpp
    
### Solve Eclipse CDT indexer unresolve inclusion problem:

* Right click Project-> Properties-> Paths and Symbols -> Includes in GNU c++:

  * add GeneratedCode Path ../GeneratedCode and ../GeneratedCode/IEC61970
  * add glib-2.0 Path /usr/include/glib-2.0
  * add glibmm-2.4 Path /usr/include/glibmm-2.4

* If Eclipse CDT indexer does not know c++11 containers, try:
  * http://stackoverflow.com/questions/17131745/eclipse-cdt-indexer-does-not-know-c12-containers
