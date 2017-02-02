# CIM2Mod

This tool is used to convert CIM-XML-RDF files into Modelica code.

## Dependencies:
* cmake >=3.6
* clang
* Boost >= 1.60.0
* ctemplate >= 2.3
* libconifg++
* CIMParser-arabica
* Doxygen

## Linux/Ubuntu:

### Install cmake:

##### From Ubuntu package:
    sudo apt-get install cmake 
    
##### Install lastest cmake version:
    wget https://cmake.org/files/v3.7/cmake-3.7.2.tar.gz
    tar xzvf cmake-3.7.2.tar.gz
    cd cmake-3.7.2/
    Install it by running:
    ./bootstrap
    make -j4
    sudo make install

### Install clang:

    sudo apt-get install clang
    
### Get the required libraries:

    sudo apt-get update
    sudo apt-get install build-essential g++ python-dev autotools-dev libicu-dev build-essential libbz2-dev libboost-all-dev

    
#### Install ctemplate:

    sudo apt-get install libctemplate-dev
    
#### Install Doxygen on Ubuntu:

	sudo apt-get install doxygen

#### Install libconfig++ on Ubuntu:

    sudo apt-get install libconfig++-dev


### To build the CIM2Mod using cmake by following steps:

#### Get CIM-XML-Parser and GridData submodule:

    git submodule update --init --recursive
    
##### if it doesn't work
    
    git submodule add https://git.rwth-aachen.de/CIM-XML-Interface/CIM-XML-Parser.git

#####  or just copy CIM-XML-Parser project into the CIM2Mod folder
    
    see https://git.rwth-aachen.de/CIM-XML-Interface/CIM-XML-Parser

#### Build CIM-XML-Parser and CIM2Mod

##### 1. Create build directory

    mkdir build

##### 2. Change into build directory and run cmake

    cd build/
    cmake -DCMAKE_BUILD_TYPE=Release ..

##### 3. Compile CIM2Mod and CIMParser

    make -j4

##### 4. [optional] Generate doxygen documentation

    make doc

#### Usage:

    cd build/bin

##### To parse separate xml files:

    ./CIM2Mod -f <file2.xml> <file2.xml>... [output_file_name] 

##### to parse all xml files in a folder:

    ./CIM2Mod -a <xml_directory/> [output_file_name]
    
  The tool generates the modelica document: `output_file_name.mo`
  
##### Command help:

    ./CIM2Mod --help

***

***
## For developers:

### update submodule:
    1. cd suibmodule directory
    2. git checkout master or git checkout release
    3. git pull
    4. git submodule update

### Recommand using clion IDE with cmake build system: 

* Makefile will not be used any more because arabica xml parser

### Solve Eclipse CDT indexer unresolve inclusion problem:

* Right click Project-> Properties-> Paths and Symbols -> Includes in GNU c++:

  * add GeneratedCode Path ../GeneratedCode and ../GeneratedCode/IEC61970
  * add glib-2.0 Path /usr/include/glib-2.0
  * add glibmm-2.4 Path /usr/include/glibmm-2.4

* If Eclipse CDT indexer does not know c++11 containers, try:
  * http://stackoverflow.com/questions/17131745/eclipse-cdt-indexer-does-not-know-c12-containers
