---
description: Written by Jonas Johansson
---

# Dinoflagellates

Dinoflagellates single-celled protists, a diverse collection of **organisms**, part of the **plankton** community and usually considered **algae**. Dinoflagellates are capable of **photosynthesis** \(converting light energy into "fuel"\) and are thus considered plants. Some exhibit bioluminescence, a process involving a light-emitting molecule and an enzyme, generally called the luciferin \(coined by[ Raphaël Dubois](https://en.wikipedia.org/wiki/Rapha%C3%ABl_Dubois)\). 

Dinoflagellates can be cultivated and purchased from places such as [Pyrofarms](https://pyrofarms.com/) \(US\) and [Bioglow](https://bioglow.eu/) \(Europe\). The former provide excellent instructions and information:

* [PyroDino instructions](https://pyrofarms.com/pages/pyrodino-instructions)
* [Bio-Orb instructions](https://pyrofarms.com/pages/bio-orb-instructions)
* [Grow your own Dinos](https://pyrofarms.com/blogs/pyrofarms-blue-light-special/grow-your-own-dinos)
* [What is a dinoflagellate](https://pyrofarms.com/pages/what-is-a-dinoflagellate)
* [Dinoflagellate FAQ](https://pyrofarms.com/pages/faq)

![PyroDinos from Pyrofarms](https://cdn.shopify.com/s/files/1/0016/8961/6442/products/Bio-Orb_swirl_wave_1024x1024@2x.jpg?v=1568988404)

Also visit the [dinoflagellate culturing](https://scripps.ucsd.edu/labs/mlatz/bioluminescence/dinoflagellates-and-red-tides/dinoflagellate-culturing/) page fro the SCRIPPS Institute of Oceanography and the UCSB [growing your own dinoflagellates](https://biolum.eemb.ucsb.edu/organism/dinohome.html).

## Alter Circadian Rhythm

It is often said that growing dinoflagellates is a lot like taking care of a plant. However, I would disagree. Perhaps on a technical level, there are many similarities, but I find that the dinoflagellates require much more consideration.

Dinoflagellates perform photosynthesis during daytime hours and only produce the light during their dark cycle at night. Program the light timer for 12 hours of light and make sure they are in the dark during the other 12 hour cycle. It usually takes a couple of days, maybe a week, before they begin to change their cycle.

#### Materials

* 1x [Digital timer](https://www.kjell.com/se/produkter/el-verktyg/el-produkter/starkstrom/timers-klockstrombrytare/luxorparts-digital-timer-7-dygn-p50002)
* 1x [LED lamp](https://www2.meethue.com/sv-se/p/hue-white-ambiance-1-pack-e27/8718699673147)
* 1x [E27 power base](https://www.clasohlson.com/se/Lamph&aring;llare-med-tygkl&auml;dd-sladd-Northlight/p/36-6234)

## Activate Bioluminescence

Bioluminescence is expressed when the dinos are gently agitated and physically moved. This can be done in a few ways:

1. Gently moving the container to create a swirling motion
2. By creating a water vortex \([Instructable](https://www.instructables.com/id/Water-Vortex-Mini-Fountain/)\) with either a pump or [magnets](https://www.youtube.com/watch?v=PcPpBiHEcwM) \([Instructable](https://www.instructables.com/id/How-to-Make-a-Cheap-Portable-Magnetic-Stirrer/)\).

### Building a Magnetic Stirrer

Since you most likely want to keep maintenance to a minimum, building a water vortex with magnets is an effective way to create movement.

{% embed url="https://www.youtube.com/watch?v=Xqkt1-6\_B2E" %}

#### Materials

* [4x Magnets](https://www.kjell.com/se/produkter/hem-kontor-fritid/gadgets/neodymmagnet-12-mm-6-pack-p50071) \(power is determined by the body of water moved\)
* 1x [12V fan](https://www.kjell.com/se/produkter/el-verktyg/elektronik/elektromekanik/flaktar/12-v/axialflakt-12-v-120x120x25-mm-p36204)
* 1x [12V power supply](https://www.kjell.com/se/produkter/el-verktyg/stromforsorjning/natadaptrar/acdc-natadaptrar/fast-utspanning/switchat-nataggregat-12-v-dc-36-w-p44384)
* 1x [DC jack](https://www.kjell.com/se/produkter/el-verktyg/el-produkter/svagstrom/dc-kontakter/terminalblock-med-dc-hona-55x21-mm-p39981?gclid=CjwKCAjwv4_1BRAhEiwAtMDLsv4SiYbSCRgMsg7CMbhtTipfVk8V5codL_YRp8zyOX9KYDioHGEHFBoC6mgQAvD_BwE&gclsrc=aw.ds)

#### Steps

1. Attach magnet 1 and 2 on opposite ends on the fan, with reverse polarity \(positive on one side, negative on the other\). 
2. Take magnet 3 and 4 and place them side by side and cover them in polymorph \(a type of mouldable plastic\) to create a pill like shape. It is fine to cover them in tape. The wider the shape, the wider the vortex.
3. Drop the combined magnets into a container of water, a bit larger than the space covered by the magnets on the fan.
4. Connect the fan to the jack, and finally to the power supply.
5. Hold the container centred over the fan, and the magnets should begin spinning, creating a vortex!

{% hint style="danger" %}
The speed of the fan at full power is too powerful for the dinoflagellates and will kill them. Make sure to reduce the power to an optimal level using a potentiometer or a micro-controller.
{% endhint %}

### Making it interactive

This assumes you have the basics in order; Some soldering equipment, an [Arduino Uno](https://www.kjell.com/se/produkter/el-verktyg/arduino/utvecklingskort/playknowlogy-uno-rev.-3-arduino-kompatibelt-utvecklingskort-p88860) and [USB-B cable](https://www.kjell.com/se/produkter/dator/kablar-adaptrar/usb/usb-kablar/usb-b-kabel-svart-18-m-p98610), a [breadboard](https://www.m.nu/breadboarding/breadboard-half-size-solderless) and some [male/male jumper wires](https://www.m.nu/breadboarding/breadboarding-premium-male-male-jumper-wires-40-x-6-150mm).

Then, make sure to get:

* 1x [TIP120 NPN Power Darlington Transistor](https://www.m.nu/ic-transistorer/tip120-npn-power-darlington-transistors-3-pack)
* 1x [1N4001 diode](https://www.m.nu/blandat/1n4001-diode-10-pack)
* 1x 2.2kOhm resistor
* 1x sensor of choice, for instance a [Touch Sensor](https://www.m.nu/knappar/standalone-momentary-capacitive-touch-sensor-breakout-at42qt1010)

#### Steps

Follow [this guide](https://bildr.org/2011/03/high-power-control-with-arduino-and-tip120/) for hooking up the fan to the Arduino, and you should have in interactive magnetic stirrer!

{% hint style="info" %}
A great reason for using a micro-controller is the possibility to build in a timer, since the dinoflagellates need time between activation before they can express their bioluminescence.
{% endhint %}

