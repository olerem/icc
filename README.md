# icc
inter chip communication

Information collection for different Interchip and Intra Chip communication

Examples of Interchip Chip Communication:
- MCU to CPU bridge - Arduino Yún
- EC to CPU on x86 platforms
- ath9k-htc and other atheros Host To Chip bridges (p2p multip port)
- Nokia n900, linux/driver/hsi (p2p multiport)
- I2CSec http://www.sciencedirect.com/science/article/pii/S1383762110001633
- IC-USB https://en.wikipedia.org/wiki/InterChip_USB
- TI HDQ? http://www.ti.com/lit/an/slua408a/slua408a.pdf
- GSM.07.10 (gsmmux) linux/drivers/tty/n_gsm.c
- 3964R/3964 + RK512 (Siemens?) linux/drivers/tty/n_r3964.c


Intra Chip Communication
- Different variants of Virtualisation

-----------------------------------------------
- Name,        HIF/PHY,       Transport
- ath9k-htc,    USB,             OSI2(HTC) + OSI3(WMI)
- ath10k,       PCIe,            HTC
- ath6kl,       SDIO,            HTC
- n900,         OMAP HSI,        ???
- n_gsm.c	TTY		 gsmmux
- n_3964	TTY		OSI2 (3964r) + OSI3(RK512)


What is the difference between plain master slave communication and ICC? Abstraction level?
Plaint Master-Slave: Slave_HW->Master_Bus->Bus_Driver->Slave_Driver
ICC: Diff_functionalities->Slave_HW->Master_Bus->Bus_Driver->Multiple_Func_drivers
