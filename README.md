
```sh
rm -rf build

cmake --preset=Release
cmake --build --preset=Release

cmake --preset=Debug
cmake --build --preset=Debug


~/STM32CubeProgrammer/bin/STM32_Programmer_CLI -c port=SWD -d build/Release/STM32F429I.elf -v -hardRst

```
