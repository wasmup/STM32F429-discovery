# STM32F429I-DISCOVERY CortexM4F 168MHz MB1075 B-01

```sh
sudo apt update
sudo apt install -y gcc-arm-none-eabi openocd build-essential git
arm-none-eabi-gcc --version

rm -rf build

cmake --preset=Release
cmake --build --preset=Release

cmake --preset=Debug
cmake --build --preset=Debug


~/STM32CubeProgrammer/bin/STM32_Programmer_CLI -c port=SWD -d build/Release/STM32F429I.elf -v -hardRst


# arm-none-eabi-objcopy -I binary -O ihex --change-section-address .data=0x08000000 blink.bin blink.hex
arm-none-eabi-objcopy -O ihex build/Release/STM32F429I.elf build/Release/STM32F429I.hex
openocd -f board/stm32f429discovery.cfg -c "adapter speed 1800" -c "init" -c "reset init" -c "program build/Release/STM32F429I.hex verify" -c "reset run" -c "shutdown"

```
