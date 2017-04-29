Nitrokey Storage Firmware
=========================

## Building

### Windows

Note: This works with Windows 7. Newer Windows versions may not work.

Install the following tools in this order:

1. [avr32-gnu-toolchain-2.4.2-setup.exe](http://www.atmel.com/System/BaseForm.aspx?target=tcm:26-17439)
1. [avr32studio-ide-installer-2.5.0.35-win32.win32.x86.exe](http://www.atmel.com/tools/studioarchive.aspx)
1. [AvrStudio4Setup.exe](http://www.atmel.com/tools/studioarchive.aspx)
1. [AVRStudio4.18SP2.exe](http://www.atmel.com/System/BaseForm.aspx?target=tcm:26-41051)

### Linux

#### Dependencies

Download and extract the following file:

1. A working Java Runtime Environment (JRE)
1. [avr32studio/R2.6.0/as4e-ide-2.6.0.753-linux.gtk.x86_64.zip](http://distribute.atmel.no/tools/avr32/old/avr32studio/R2.6.0/as4e-ide-2.6.0.753-linux.gtk.x86_64.zip)

    cd as4e-ide
    chmod -R +x Plugins/com.atmel.avr* # Make the binaries runnable
    chmod +x avr32studio
    ./avr32studio

#### Importing the project

Follow the following sequence:

    File -> Import -> General -> Existing Projects into Workspace

Then point the root directory to the nitrokey-storage-firmware directory. It
will then find the STICK20_GIT project.

After this is done, try building the project by pressing Ctrl + B. This should
succeed.

#### Converting the output for flashing

In the nitrokey-storage-firmware, you should now have a Debug/ folder, created by
the compilation. Inside, you should find the file 'USB_MASS.elf' there.

Let's convert it into ihex, so as to be flashable:

    avr-objcopy -R .eeprom -O ihex USB_MASS.elf firmware.hex

That's all folks!

## Flashing the Firmware to Device

- [Latest firmware releases](https://github.com/Nitrokey/nitrokey-storage-firmware/tree/master/binary)
- [Firmware upgrade instructions](https://www.nitrokey.com/en/doc/firmware-update-storage)
