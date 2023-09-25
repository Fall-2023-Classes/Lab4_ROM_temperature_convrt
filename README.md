# Lab4_ROM_temperature_convrt
Using two 0.5 Block RAMs to store two ROM memories for Celsius and Fahrenheit conversion values. Range from 0 to 100C, 32 to 212F.

[Lab 4 Files]()

## Temperature Converter
![Temperature Converter Block Diagram]()

The point of this lab is to minimize the amount of resources used on our FPGA board. An example of this is to force a [ROM module]() to use the BRAM on the FPGA board instead of using the LUTs. We created a simple [temperature conversion]() tool that uses ROM to store the values for the conversions, either from Celsius to Fahrenheit or vice versa. In this case, we instantiated two of these [ROM modules](), each using 0.5 BRAM on the board. By having both conversion values go through a [2x1 multiplexer](), we can easily switch between converting from Celsius values or from Fahrenheit values. This converted temperature value in binary will go through a [binary to BCD converter]() before going through the [seven-segment controller]() and finally outputting on the board.

  - [Temperature Converter TOP file]()
    - [Temperature Converter TOP Test Bench Simulation File]()
  - [ROM]()
  - [2x1 MUX]()
  - [bin2bcd]()
  - [seven seg control]()
    - [modulus counter]()
    - [seven_seg_control Test Bench Sim]()
  - [sevSegDec]()

      
    

    
## ROM
![image]()

This lab uses a simple Read Only Memory module that is modified in a specific way to force Vivado to use the BRAM on the FPGA board instead of the LUTs. We use two of these modules to store the conversion values for Celsius and Fahrenheit temperatures. The Lookup Tables for these values ([truth_table_celsius.mem]() and [truth_table_fahrenheit.mem]()) are manually created using Excel.

- [ROM Module]()
  - [LUT for Celsius values]()
  - [LUT for Fahrenheit values]()


