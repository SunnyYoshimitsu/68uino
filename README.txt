# 68uino

I started the project sometime after watching a video by Ander Nielson (link below) and got the idea of making something similar. 

Inspiration: https://www.youtube.com/watch?v=s3t2QMukBRs&t=563s&ab_channel=AndersNielsen

However, since he already did the 6502, I decided to use a different processor to challenge myself. Whilst browsing through Jamesco, I found the 6802, a 6800-based CPU. It was very similar to the 6502 due to being designed by the same engineers and most importantly, it had built-in RAM. Doing more research left me with the HD6303 which was the same as the 6202 except with more built-in peripherals. With this chip, I believe I could make a computer even smaller than that of Mr.Nielson's. 

The datasheet of the processor(6303) however had many flaws, like all the odd pages being shown in the beginning and everything else at the end. So I painstakingly reorganized everything start with. The datasheet is posted along with other files here. 

The peripherals on the HD6303 are crazily packed to make it an MCU if not for its lack of ROM. 
Peripherals:
	Timer
	2 GPIO Ports
	Built-in RAM (128 byte)
	built-in clock circuit
	Non-volatile RAM

As one can see, we can already omit GPIOs, RAMs, UART, and timer chips in this design. This makes for a very compact and easy-to-developed system. 

There are two versions of this particular chip. The non-multiplexed 64 pins and the multiplexed 40 pins chip. I've chosen the 40 pin versions for their size, however, that will require me to use a 74ls373 chip to be able to use the multiplexed circuitry, similar to the i8088. Below are the links to the 64 pins(Jamesco), I got my 40 pins from eBay. 

https://www.jameco.com/z/HD6303YP-HITACHI-IC-6303YP-CMOS-8-Bit-MPU-Micro-Processing-Unit-_2287967.html

Designing the system itself, I've decided to make the system compact enough to fit on an Arduino form-factor perf-shield(link below) and running at 1MHz. This is for prototyping purposes and I might move to printing PCBs after since it's cheap provided we use small sizes and in small quantities. 

https://www.aliexpress.us/item/2251832487864030.html?spm=a2g0o.home.0.0.135076db3SfYPj&mp=1&gatewayAdapt=glo2usa

Just making an MCU in itself is very fun, but I also want to make a "field-programmable" MCU to make it a bit more challenging. This meant making a serial monitor program, a human interface, and having an input. I decided to add an SSD1306 screen similar to how Mr.Nielson did his and to add a keyboard interface. Now, in the modern-day, all keyboards are USB-based which is very hard to achieve using a slow and ancient processor. Hence, I opted for the P/S2 interface with a relatively simple architecture. The hope is that I could use that keyboard and type into a monitor program (think WozMon) and it will display on the SSD1306. 

Enough about the ideas and the CPU, let's talk about the system memory layout. This CPU is an 8bit CPU and like the 6502 can only access up to 64k of memory. 

Memory Layout: 
0000 - 001F: Internal Peripheral Registers
001F - 0080: 	Empty
0080 - 00FF: RAM 
6000 - 7FFF: 	Empty
8000 - FFFF: ROM 

And lastly, here's the chips used in this project:
1x 74LS373
1x Ne555
1x 27c256
1x HD6303
1x 4MHz Crystal


Welp....at least that's the plan, I've yet to put it on a per-board and will update when I finish. Thanks for checking this Git/Post!!!!


If you have any question or ideas please don't hesitate to hit me up! I am an active user in the r/beneater subreddit. 
Profile: https://www.reddit.com/user/YoshimitsuSunny