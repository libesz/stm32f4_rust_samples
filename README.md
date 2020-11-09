# stm32f4_rust_samples
Sample rust applications for the low cost black pill board.

I am not a Rust expert (yet :) ), so that this repo contains my first attempts to run Rust code on the WeAct 3.0 low-cost STM32F4 black pill board. The board comes in a wide variety. Mine has an STM32F401CEU6 MCU.
There are similar repos out there, so I aligned some of them to this board (i.e. different LED and switch locations) to have everything ootb working.

Prepare:
* You need Rust nightly: `rustup default nightly`
* You need Rust objcopy to strip ELFs into raw binaries: `cargo install cargo-binutils`
* You need DFU utils to upload the binaries using the pre-programmed bootloader on this board (can be found in platform.io utils) 

Build:
* You can directly build the raw binary files using their target name in the `Cargo.toml`, like: `cargo objcopy --bin button_led_blink --release -- -O binary button_led_blink`

Install:
* Put your board into DFU bootloader mode, if available
* Use dfu-util to upload the raw binary: `"~/.platformio/packages/tool-dfuutil/bin/dfu-util" -d 0x0483:0xDF11 -a 0 -s 0x08000000:leave -D ./button_led_blink`

Ref:
* [Board docs](https://github.com/WeActTC/MiniF4-STM32F4x1/)

Contribution:
Feel free to contribute any missing instruction, fix or new sample for this board.
