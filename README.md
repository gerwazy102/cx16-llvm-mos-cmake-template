# cx16-llvm-mos-cmake-template

This is a simple template to get started with C/C++ projects for Commander X16 using cmake + llvm mos sdk.

## Prerequisites

1. Cmake installed
2. Newest release of llvm-mos-sdk from here: https://github.com/llvm-mos/llvm-mos-sdk - follow install instructions here.
3. Optionally visual studio code with CMake, CMake Tools and C/C++ extensions.

## How to customize?

There are 2 lines in `CMakeLists.txt` which you can easily customize:

```cmake
set(PROJECT_NAME TEMPLATE)
set(ENTRY_FILE main.cpp)
```

`PROJECT_NAME` - this affects output file name - by default `./bin/TEMPLATE.PRG` will be generated

`ENTRY_FILE` - points to main c++ entrypoint file

## How to run from terminal?

```bash
cmake --no-warn-unused-cli -DCMAKE_PREFIX_PATH= <PATH_TO_LLVM-MOS> -DCMAKE_BUILD_TYPE:STRING=MinSizeRel -DCMAKE_EXPORT_COMPILE_COMMANDS:BOOL=TRUE -S ./ -B./build -G Ninja

cd build
ninja
```
or

```bash
cmake --no-warn-unused-cli -DCMAKE_PREFIX_PATH= <PATH_TO_LLVM-MOS> -DCMAKE_BUILD_TYPE:STRING=MinSizeRel -DCMAKE_EXPORT_COMPILE_COMMANDS:BOOL=TRUE -S ./ -B./build

cd build
make
```

## VSCode CMake configuration

For VSCode CMake to correctly detect LLVM-MOS you should create `.vscode/settings.json` file in workspace directory. Inside you should put following:

```json
{
  "cmake.configureArgs": [
    "-DCMAKE_PREFIX_PATH=<LLVM-MOS-INSTALL-PATH>"
  ]
}
```

## How to run?

You can run generated programs on `x16emu` or `box16` emulators:

```bash
box16 -prg bin/TEMPLATE.PRG -run #or
x16emu -prg bin/TEMPLATE.PRG -run
```

## Compiler explorer

There is an amazing tool which can show llvm-mos generated assembly on the fly! Tool is called "Compiler explorer" and is available in the browser [here!](https://godbolt.org/). Check out how `main.cpp` from this repository turns out in 6502 assembly [here!](https://godbolt.org/#g:!((g:!((g:!((h:codeEditor,i:(filename:'1',fontScale:14,fontUsePx:'0',j:1,lang:c%2B%2B,selection:(endColumn:14,endLineNumber:1,positionColumn:14,positionLineNumber:1,selectionStartColumn:14,selectionStartLineNumber:1,startColumn:14,startLineNumber:1),source:'%23include+%3Ccstdio%3E%0A%0A%0Aint+main()+%7B%0A++++std::puts(%22HELLO+WORLD!!%22)%3B%0A++++return+0%3B%0A%7D%0A'),l:'5',n:'0',o:'C%2B%2B+source+%231',t:'0')),k:49.99999999999999,l:'4',n:'0',o:'',s:0,t:'0'),(g:!((h:compiler,i:(compiler:mos-cx16-trunk,filters:(b:'0',binary:'1',binaryObject:'1',commentOnly:'0',debugCalls:'1',demangle:'0',directives:'0',execute:'1',intel:'0',libraryCode:'0',trim:'1'),flagsViewOpen:'1',fontScale:14,fontUsePx:'0',j:1,lang:c%2B%2B,libs:!(),options:'-Oz+-Wall+-Wextra+-Wno-uninitialized',overrides:!(),selection:(endColumn:31,endLineNumber:11,positionColumn:31,positionLineNumber:11,selectionStartColumn:31,selectionStartLineNumber:11,startColumn:31,startLineNumber:11),source:1),l:'5',n:'0',o:'+llvm-mos+commander+X16+(Editor+%231)',t:'0')),k:49.99999999999999,l:'4',n:'0',o:'',s:0,t:'0')),l:'2',n:'0',o:'',t:'0')),version:4)
