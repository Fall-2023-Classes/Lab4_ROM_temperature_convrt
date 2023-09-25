# Lab4_ROM_temperature_convrt
Using two 0.5 Block RAMs to store two ROM memories for Celsius and Fahrenheit conversion values. Range from 0 to 100C, 32 to 212F.

[Lab 4 Files](https://github.com/Fall-2023-Classes/Lab4_ROM_temperature_convrt/tree/main/Lab4Files)

## Temperature Converter
![Temperature Converter Block Diagram]()

The point of this lab is to minimize the amount of resources used on our FPGA board. An example of this is to force a [ROM module](https://github.com/Fall-2023-Classes/Lab4_ROM_temperature_convrt/blob/main/Lab4Files/Design/ROM.sv) to use the BRAM on the FPGA board instead of using the LUTs. We created a simple [temperature conversion](https://github.com/Fall-2023-Classes/Lab4_ROM_temperature_convrt/blob/main/Lab4Files/Design/temp_conversion.sv) tool that uses ROM to store the values for the conversions, either from Celsius to Fahrenheit or vice versa. In this case, we instantiated two of these [ROM modules](https://github.com/Fall-2023-Classes/Lab4_ROM_temperature_convrt/blob/main/Lab4Files/Design/ROM.sv), each using 0.5 BRAM on the board. By having both conversion values go through a [2x1 multiplexer](https://github.com/Fall-2023-Classes/Lab4_ROM_temperature_convrt/blob/main/Lab4Files/Design/mux_2x1.sv), we can easily switch between converting from Celsius values or from Fahrenheit values. This converted temperature value in binary will go through a [binary to BCD converter](https://github.com/Fall-2023-Classes/Lab4_ROM_temperature_convrt/blob/main/Lab4Files/Design/bin2bcd.v) before going through the [seven-segment controller](https://github.com/Fall-2023-Classes/Lab4_ROM_temperature_convrt/blob/main/Lab4Files/Design/seven_seg_control.sv) and finally outputting on the board.

  - [Temperature Converter TOP file](https://github.com/Fall-2023-Classes/Lab4_ROM_temperature_convrt/blob/main/Lab4Files/Design/temp_conversion.sv)
    - [Temperature Converter TOP Test Bench Simulation File](https://github.com/Fall-2023-Classes/Lab4_ROM_temperature_convrt/blob/main/Lab4Files/Simulation/temp_conversion_TB.sv)
  - [ROM](https://github.com/Fall-2023-Classes/Lab4_ROM_temperature_convrt/blob/main/Lab4Files/Design/ROM.sv)
  - [2x1 MUX](https://github.com/Fall-2023-Classes/Lab4_ROM_temperature_convrt/blob/main/Lab4Files/Design/mux_2x1.sv)
  - [bin2bcd](https://github.com/Fall-2023-Classes/Lab4_ROM_temperature_convrt/blob/main/Lab4Files/Design/bin2bcd.v)
  - [seven seg control](https://github.com/Fall-2023-Classes/Lab4_ROM_temperature_convrt/blob/main/Lab4Files/Design/seven_seg_control.sv)
    - [modulus counter](https://github.com/Fall-2023-Classes/Lab4_ROM_temperature_convrt/blob/main/Lab4Files/Design/mod_counter.sv)
    - [seven_seg_control Test Bench Sim](https://github.com/Fall-2023-Classes/Lab4_ROM_temperature_convrt/blob/main/Lab4Files/Simulation/seven_seg_control_TB.sv)
  - [sevSegDec](https://github.com/Fall-2023-Classes/Lab4_ROM_temperature_convrt/blob/main/Lab4Files/Design/sevSegDec.sv)

      
    

    
## ROM
![image]()

This lab uses a simple Read Only Memory module that is modified in a specific way to force Vivado to use the BRAM on the FPGA board instead of the LUTs. We use two of these modules to store the conversion values for Celsius and Fahrenheit temperatures. The Lookup Tables for these values ([truth_table_celsius.mem](https://github.com/Fall-2023-Classes/Lab4_ROM_temperature_convrt/blob/main/Lab4Files/Design/truth_table_celsius.mem) and [truth_table_fahrenheit.mem](https://github.com/Fall-2023-Classes/Lab4_ROM_temperature_convrt/blob/main/Lab4Files/Design/truth_table_fahrenheit.mem)) are manually created using Excel.

- [ROM Module](https://github.com/Fall-2023-Classes/Lab4_ROM_temperature_convrt/blob/main/Lab4Files/Design/ROM.sv)
  - [LUT for Celsius values](https://github.com/Fall-2023-Classes/Lab4_ROM_temperature_convrt/blob/main/Lab4Files/Design/truth_table_celsius.mem)
  - [LUT for Fahrenheit values](https://github.com/Fall-2023-Classes/Lab4_ROM_temperature_convrt/blob/main/Lab4Files/Design/truth_table_fahrenheit.mem)


