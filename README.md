# AtmelStudio_Using_ArduinoBootloader
This Repository Explains How to Use Arduino Bootloader in Atmel Studio 

->avrdude for AVR, Bossac for ATSAM.
## Gerneral
To use the Arduino Bootloader in Atmel Studio, This can be implement as External Tool in Atmel Studio.

### 1. Get the Execute command from the verbose output from ArduinoIDE
To show the verbose output, Check the ++upload++ checkbox in the File->Preference.
![ArduinoPreference](https://github.com/rottenCoriander/AtmelStudio_Using_ArduinoBootloader/blob/main/images/ArduinoPreference.PNG)

Perform an Upload, and you will get the Execute command form Toolchain.
![ArduinoVerboseOutout](https://github.com/rottenCoriander/AtmelStudio_Using_ArduinoBootloader/blob/main/images/ArduinoVerboseOutput.png)

### 2. Create an External Tool in Atmelstudio
Create an External Tool form Tool->External Tools in Atmel Studio
![PathExternalToos](https://github.com/rottenCoriander/AtmelStudio_Using_ArduinoBootloader/blob/main/images/PathExternalTools.png)


## AVR(avrdude)

## ATSAM(bossac)
Here you got the Toochain command for ArduinoIDE, for example (from Arduino DUE):

```
C:\Users\rottenCoriander\AppData\Local\Arduino15\packages\arduino\tools\bossac\1.6.1-arduino/bossac.exe -i -d --port=COM14 -U false -e -w -v -b C:\Users\SS2010~1\AppData\Local\Temp\arduino_build_684794/3x8etest.ino.bin -R
```

So the path of bossac.exe is where your Toolchain is, and the path with 3x8etest.ino.bin is where your build is.
and now you are goging to replce your build path to "$(ProjectDir)Debug\" and "$\(TargetName).extentions" for your build output.

So here is an example:
```
C:\Users\rottenCoriander\AppData\Local\Arduino15\packages\arduino\tools\bossac\1.6.1-arduino/bossac.exe -i -d --port=COM14 -U false -e -w -v -b "$(ProjectDir)Debug$\(TargetName).bin" -R
```

