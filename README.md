# LPS25HB_Driver

此项目基于ST官方 Platform-independent device driver for LPS25HB 代码，主要修改如下：  
1. 增加了STM32Cube HAL I2C适配方法，基于STM32Cube HAL的项目可以直接使用此Driver。
2. 修正了LPS25HB_Set_BDU和LPS25HB_Get_BDU函数名称不一致的问题。

This project is based on ST official Platform-independent device driver for LPS25HB.  
Change list：  
1. add driver function for STM32Cube HAL I2C.
2. fix the function name for LPS25HB_Set_BDU and LPS25HB_Get_BDU.

When read and write more than one bytes，this sensor requires some special requirement for the address of registers：  
此传感器在I2C连续传输数据时，对寄存器地址有一些特殊要求，以下内容摘自传感器Datasheet：

The I²C embedded in the LPS25HB behaves like a slave device and the following protocol
must be adhered to. After the start condition (ST) a slave address is sent, once a slave
acknowledge (SAK) has been returned, an 8-bit sub-address (SUB) will be transmitted: the 7
LSB represents the actual register address while the MSB enables address auto increment.
If the MSb of the SUB field is ‘1’, the SUB (register address) will be automatically increased
to allow multiple data read/write.

