# pod_plugin
Add-ons for Protocol Buffers, it change proto message to c struct 


## Clone the repository (including submodules)

```sh
git clone https://github.com/snow1313113/pod_plugin.git
cd pod_plugin
git submodule update --init

# build protobuf
cd third_party/protobuf
./autogen.sh
./configure --prefix=/usr/local/protobuf
make

# build googletest
cd third_party/googletest
mkdir build && cd build
cmake .. && make
```

## Build from source

```sh
mkdir build
cd build
cmake ../
make
```

## Use the plugin

 protoc --proto_path=*your path* --pod_out=*output path* --plugin=protoc-gen-pod=pod_plugin *proto file*

 there is some options that can specify c++ standard of gen code
 use *--pod_opt=c++98* or *--pod_opt=c++11*

## Build gtest case

```sh
cd pod_plugin/test
mkdir build
cd build
cmake ../
make
```

## Clangd
```
# to workspace build folder generate compile_commands.json file and install clangd
cmake -DCMAKE_EXPORT_COMPILE_COMMANDS=True ..
```