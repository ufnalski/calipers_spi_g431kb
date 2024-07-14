# Digital caliper (tyre tread depth gauge[^1]) reading over SPI (STM32G431KB)
An STM32 HAL example of reading over the SPI bus a tyre tread depth gauge or a pair of calipers[^2].

[^1]: The word caliper comes from latin roots meaning precise pincer. Formally, a tyre tread depth gauge is no more a pair of calipers :monocle_face: However, we are here to read the sensor itself and the etymology can be put aside as it does not affect our experiment and can be investigated later on :wink:
[^2]: Calipers, [https://en.wikipedia.org/wiki/Calipers](https://en.wikipedia.org/wiki/Calipers)

# Motivation
Pure curiosity. I used to use Vernier calipers. Roughly a decade ago (as of 2024) I switched to digital/electronic calipers. Back then they were not cheap and I restrained myself from disassembling them. Recently I was looking for a cheap, yet mechanical to have some movement (which is always more fun), SPI device to play with. If you are familiar with [Ford Mustang VI (S550) 2015+ instrument panel cluster hacking](https://github.com/ufnalski/ford_mustang_cluster_h503rb), you already know the drill :slightly_smiling_face: Engaging classrooms/labs. Hands-on training on the SPI bus communication. The price of a pair of calipers strongly depends on their measuring range. That is why the cheapest ones can be found among tyre tread depth gauges. To my surprise, a regular price offered by Polish resellers for such gauges comes out to be even as low as 3.5 EUR. A perfect educational toy your trainees can experiment with or even disassemble it to see what's inside. And you can learn some interesting stuff along the way, including the principle of operation of the sensor.

![Tyre tread depth gauge readings in inches](/Assets/Images/gauge_readings_in_inch.jpg)

![Tyre tread depth gauge readings in millimeters](/Assets/Images/gauge_readings_in_mm.jpg)

# My setup
For simplicity, I keep the original battery (LR44, 1.5 V) to power the gauge and the LV side of a logic level shifter. To reduce maintenance costs if envisaged for frequent training sessions, the battery should be replaced with an LDO regulator in the future.

# Missing files?
Don't worry :slightly_smiling_face: Just hit Alt-K to generate /Drivers/CMCIS/ and /Drivers/STM32G4xx_HAL_Driver/ based on the .ioc file. After a couple of seconds your project will be ready for building.

# Hints
The SPI bus can be configured to operate in one of the four modes[^3]: 0, 1, 2 or 3. Remember to configure the peripheral of the uC to match the mode selected by the manufacturer for the sensor. In the case of my calipers it is CPOL = 1 and CPHA = 1, i.e. Mode 3, as shown in [/Assets/Images/](/Assets/Images/).

[^3]: [Introduction to SPI Interface](https://www.analog.com/en/resources/analog-dialogue/articles/introduction-to-spi-interface.html) (Analog Devices)

# If you are curious what's inside and how it works
* [How Does A Digital Caliper Work?](https://www.youtube.com/watch?v=u84BDCo22U4) (learnelectronics)
* [Inside a cheap set of eBay digital calipers](https://www.youtube.com/watch?v=fKSSY1gzCEs) (bigclivedotcom)
* [Jak dziala elektroniczna suwmiarka?](https://www.youtube.com/watch?v=LB3j4dgQaBE) (RS Elektronika, in Polish)
* [Digital Caliper HACK/MOD from 150mm to 650mm](https://www.youtube.com/watch?v=JYnit_PSSMY) (Limi DIY)
* [Jak działa suwmiarka elektroniczna](https://www.elektroda.pl/rtvforum/topic4033452.html) (elektroda, in Polish)
* [U.S. Patent No. 4,586,260: Capacitive displacement measuring instrument](https://patentimages.storage.googleapis.com/a3/12/d1/f02db4403cb5a8/US4586260.pdf)

# Exemplary hardware for breadboarding
* [Logic Level Converter TXS0108E](https://www.az-delivery.de/en/products/logiklevel-wandler-3-3v-5v) (AZ-Delivery)

# Similar projects
* [Caliper and Arduino I2C - measure 3D filament](https://www.youtube.com/watch?v=tTV52DihPTc) (Electronoobs)[^4]
* [Reading Digital Callipers With an Arduino / USB](https://www.instructables.com/Reading-Digital-Callipers-with-an-Arduino-USB/) (Instructables)
* [Hacked Digital Vernier Caliper Using Arduino](https://www.instructables.com/Hacked-Digital-Vernier-Caliper-Using-Arduino/) (Instructables)

[^4]: It should be renamed to SPI. The I2C bus introduces addressing which is not the case here.

# Sources/libraries
* OLED: [stm32-ssd1306](https://github.com/afiskon/stm32-ssd1306) (MIT license)

# Call for action
Create your own [home laboratory/workshop/garage](http://ufnalski.edu.pl/control_engineering_for_hobbyists/2024_dzien_otwarty_we/Dzien_Otwarty_WE_2024_Control_Engineering_for_Hobbyists.pdf)! Get inspired by [ControllersTech](https://www.youtube.com/@ControllersTech), [DroneBot Workshop](https://www.youtube.com/@Dronebotworkshop), [Andreas Spiess](https://www.youtube.com/@AndreasSpiess), [GreatScott!](https://www.youtube.com/@greatscottlab), [ElectroBOOM](https://www.youtube.com/@ElectroBOOM), [Phil's Lab](https://www.youtube.com/@PhilsLab), [atomic14](https://www.youtube.com/@atomic14), [That Project](https://www.youtube.com/@ThatProject), [Paul McWhorter](https://www.youtube.com/@paulmcwhorter), and many other professional hobbyists sharing their awesome projects and tutorials! Shout-out/kudos to all of them!

> [!WARNING]
> Control engineering - try this at home :exclamation:

190+ challenges to start from: [Control Engineering for Hobbyists at the Warsaw University of Technology](http://ufnalski.edu.pl/control_engineering_for_hobbyists/Control_Engineering_for_Hobbyists_list_of_challenges.pdf).

Stay tuned :exclamation:
