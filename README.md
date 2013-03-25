The Spark Socket
=====

These are the design files for the Spark Socket, developed by Hex Labs, Inc. dba Spark Devices.

These files have been made available online through a [Creative Commons Attribution-ShareAlike 3.0](http://creativecommons.org/licenses/by-sa/3.0/) Unported license.

You are welcome to distribute, remix, and use these files for commercial purposes. If you do so, please attribute the original design to Spark Devices both on the website and on the physical packaging of the product or in the instruction manual. All derivitive works must be published under the same or a similar license.

## The Story

Development of the Spark Socket began in December, 2011, sparked (sorry) by a conversation over dinner in a Japanese restaurant with Zach's then-girlfriend's (now fiancee's) parents. Over the next eleven months, Spark went from an idea to a product. On November 13, 2012, the Spark Socket was published on the crowdfunding platform Kickstarter. The Kickstarter campaign site can be found [here](http://www.kickstarter.com/projects/sparkdevices/spark-upgrade-your-lights-with-wi-fi-and-apps).

The Spark Socket Kickstarter campaign ran from November 13, 2012 to December 13, 2012. In that time, roughly 1,600 individuals devoted their time and money to supporting Spark with a total of $125,588 pledged. The funding threshold, however, for the campaign was $250,000. Because that threshold was not reached by the end of the campaign, the campaign closed unsuccessfully, and no credit cards were charged.

The Spark team continued to work on the Spark Socket after the close of the campaign, taking pre-orders on [their website](http://www.sparkdevices.com) . Between December 13, 2012 and March 25, 2013, orders for ~1,800 Spark Sockets were placed; many were from previous Kickstarter backers, and many more were from newcomers.

On March 25, 2013, the Spark team announced that they would be discontinuing development work on the Spark Socket. The design files for the product were released here on github for others to use and learn from.

## What's Included

This distro contains two versions of the Spark Socket, named Version 1 and Version 2.

Version 1 of the Spark Socket is the version that was showcased in our Kickstarter video. The design includes four circuit boards, wrapped in a cuboid shape around the inner core of the plastic enclosure.

As development on the Socket continued, Version 2 of the Spark Socket was created. Version 2 re-oriented the design so that there are only two circuit boards: one with the high voltage components of the circuit, the other with the low voltage components of the circuit. This design made integrating the power supply much easier, and would be significantly easier to assemble. It also had enough empty space that the plastic enclosure could theoretically be made smaller, although development efforts stopped before the outer enclosure was changed.

## Basic structure

The design of the Spark Socket includes four major subsystems:

- **Power supply**. The Socket sources the power for its circuitry directly from the high-voltage AC line to which it is attached. Although this may be possible with an isolated switch-mode power supply, we chose a non-isolated design to save on the bill of materials and to save space. The power supply must be able to source at least 300mA of current (mostly for the transmit events of the Wi-Fi module), although the average power draw should be closer to 50mA.
- **Micro-controller**. Because the Spark Socket was originally built using an Arduino, the micro-controller we are using is an Atmel ATmega328p. This is a low-cost 8-bit micro-controller that is very easy to develop for. For encrypted communications, a 32-bit micro-controller (such as an STM32 Cortex M3) may be used instead.
- **Wi-Fi module**. For the Socket prototype, we used a Roving Networks RN-171 Wi-Fi module. These modules are great because they are very easy to work with and get up and running quickly. They are, however, quite expensive; even with high volumes, the order price was greater than $15. Spark will be using the Texas Instruments CC3000 Wi-Fi module in our other projects, which is smaller, lower cost, and has a simpler set-up process. We recommend the CC3000 for ongoing development work.
- **TRIAC Dimmer**. The most tried-and-true way to dim a light bulb is using a TRIAC. A zero-cross detector informs the micro-controller of the timing of the AC current, and the TRIAC dimmer is activated at a specificied time interval after the zero-cross, based on the chosen dim level. TRIAC dimmers work best with resistive loads (such as incandescent bulbs), and will also work with CFLs that are labeled "dimmable" as well as LED bulbs that are labeled "dimmable". TRIAC dimmers are also called "leading edge" dimmers.