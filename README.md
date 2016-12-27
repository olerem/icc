# icc
inter chip communication

Possible client drivers:
- char (generic, do what you wont)
- gpio extender
- rtc
- watchdog
- CAN
- rfkill

Notest:
- determenistic (to avoid real-time word).
- async. Sync communication on linux is expensive. (async need timeout to responde. Async need timout to responde as well, why should we wait any way?)
- agregation. most communications use tiny packets. tiny packets are very expensive.
- queue. aggregation is possible only with a queue.

Information collection for different Interchip and Intra Chip communication

TODO: 3946R, RK512, Modbus, IEC870, MEWTOCOL, AK, MPI, LSV2, Interbus, DeviceNet, MSV2:

Examples of Interchip Chip Communication:
- MCU to CPU bridge - Arduino Yún
- EC to CPU on x86 platforms
- ath9k-htc and other atheros Host To Chip bridges (p2p multip port)
- Nokia n900, linux/driver/hsi (p2p multiport)
- I2CSec http://www.sciencedirect.com/science/article/pii/S1383762110001633
- IC-USB https://en.wikipedia.org/wiki/InterChip_USB
- TI HDQ? http://www.ti.com/lit/an/slua408a/slua408a.pdf
- GSM.07.10 (gsmmux) linux/drivers/tty/n_gsm.c
- 3964R/3964  (Siemens?) linux/drivers/tty/n_r3964.c
- RK512 https://support.industry.siemens.com/cs/document/12932189/differences-between-protocols-3964(r)-and-rk-512?dti=0&lc=en-WW
- or 3964 + RK512?  --- (- high overhead for simple p2p communication)
- LininoIO http://www.linino.org/wordpress/wp-content/uploads/2015/02/Fosdem_LininoIO.pdf
- mcuIO https://github.com/linino/kernel_3.3.8/tree/master/drivers/mcuio
	https://github.com/ciminaghi/bathos-mcuio
- WeIO USB + ttyACM + UPER https://github.com/8devices/UPER/wiki/UPER-function-list
- Texas Instruments Shared Transport driver for UART: drivers/misc/ti-st/st_core.c
- CPU to Application CPU Interface:
	https://www.kernel.org/doc/Documentation/networking/caif/Linux-CAIF.txt
	http://lxr.free-electrons.com/source/drivers/net/caif/caif_serial.c#L393
	https://lwn.net/Articles/371017/


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
