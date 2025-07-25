# Raspberry pi Camera
**Official Documentation: https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/accessories/camera/camera_hardware.adoc**
## About the Camera Modules

There are now several official Raspberry Pi camera modules. The original 5-megapixel model was https://www.raspberrypi.com/news/camera-board-available-for-sale/[released] in 2013, it was followed by an 8-megapixel https://www.raspberrypi.com/products/camera-module-v2/[Camera Module 2] which was https://www.raspberrypi.com/news/new-8-megapixel-camera-board-sale-25/[released] in 2016. The latest camera model is the 12-megapixel https://raspberrypi.com/products/camera-module-3/[Camera Module 3] which was https://www.raspberrypi.com/news/new-autofocus-camera-modules/[released] in 2023. The original 5MP device is no longer available from Raspberry Pi. 

All of these cameras come in visible light and infrared versions, while the Camera Module 3 also comes as a standard or wide FoV model for a total of four different variants.

.Camera Module 3 (left) and Camera Module 3 Wide (right)
image::images/cm3.jpg[Camera Module 3 normal and wide angle]

.Camera Module 3 NoIR (left) and Camera Module 3 NoIR Wide (right)
image::images/cm3_noir.jpg[Camera Module 3 NoIR normal and wide angle]

Additionally, a 12-megapixel https://www.raspberrypi.com/products/raspberry-pi-high-quality-camera/[High Quality Camera] with CS- or M12-mount variants for use with external lenses was https://www.raspberrypi.com/news/new-product-raspberry-pi-high-quality-camera-on-sale-now-at-50/[released in 2020] and https://www.raspberrypi.com/news/new-autofocus-camera-modules/[2023] respectively. There is no infrared version of the HQ Camera, however the xref:camera.adoc#filter-removal[IR Filter can be removed] if required.

.HQ Camera, M12-mount (left) and C/CS-mount (right)
image::images/hq.jpg[M12- and C/CS-mount versions of the HQ Camera]

The Raspberry Pi AI Camera uses the Sony IMX500 imaging sensor to provide low-latency and high-performance AI capabilities to any camera application. Tight integration with xref:../computers/camera_software.adoc[Raspberry Pi's camera software stack] allows users to deploy their own neural network models with minimal effort.

image::images/ai-camera-hero.png[The Raspberry Pi AI Camera]

Finally, there is the Global Shutter camera, which was http://raspberrypi.com/news/new-raspberry-pi-global-shutter-camera[released in 2023]. There is no infrared version of the GS Camera, however the xref:camera.adoc#filter-removal[IR Filter can be removed] if required.

.Global Shutter Camera
image::images/gs-camera.jpg[GS Camera]

NOTE: Raspberry Pi Camera Modules are compatible with all Raspberry Pi computers with CSI connectors.

=== Rolling or Global shutter?

Most digital cameras, including our Camera Modules, use a **rolling shutter**: they scan the image they're capturing line-by-line, then output the results. You may have noticed that this can cause distortion effects in some settings; if you've ever photographed rotating propeller blades, you've probably spotted the image shimmering rather than looking like an object that is rotating. The propeller blades have had enough time to change position in the tiny moment that the camera has taken to swipe across and observe the scene.

A **global shutter**, like the one on our Global Shutter Camera Module, doesn't do this. It captures the light from every pixel in the scene at once, so your photograph of propeller blades will not suffer from the same distortion.

Why is this useful? Fast-moving objects, like those propeller blades, are now easy to capture; we can also synchronise several cameras to take a photo at precisely the same moment in time. There are plenty of benefits here, like minimising distortion when capturing stereo images. (The human brain is confused if any movement that appears in the left eye has not appeared in the right eye yet.) The Raspberry Pi Global Shutter Camera can also operate with shorter exposure times - down to 30µs, given enough light - than a rolling shutter camera, which makes it useful for high-speed photography. 

NOTE: The Global Shutter Camera's image sensor has a 6.3mm diagonal active sensing area, which is similar in size to Raspberry Pi's HQ Camera. However, the pixels are larger and can collect more light. Large pixel size and low pixel count are valuable in machine-vision applications; the more pixels a sensor produces, the harder it is to process the image in real time. To get around this, many applications downsize and crop images. This is unnecessary with the Global Shutter Camera and the appropriate lens magnification, where the lower resolution and large pixel size mean an image can be captured natively.

== Install a Raspberry Pi camera

WARNING: Cameras are sensitive to static. Earth yourself prior to handling the PCB. A sink tap or similar should suffice if you don't have an earthing strap.

=== Connect the Camera

Before connecting any Camera, shut down your Raspberry Pi and disconnect it from power.

The flex cable inserts into the connector labelled CAMERA on the Raspberry Pi, which is located between the Ethernet and HDMI ports. The cable must be inserted with the silver contacts facing the HDMI port. To open the connector, pull the tabs on the top of the connector upwards, then towards the Ethernet port. The flex cable should be inserted firmly into the connector, with care taken not to bend the flex at too acute an angle. To close the connector, push the top part of the connector down and away from the Ethernet port while holding the flex cable in place.

The following video shows how to connect the original camera on the original Raspberry Pi 1:

video::GImeVqHQzsE[youtube,width=80%,height=400px]

All Raspberry Pi boards with a camera connector use the same installation method, though the Raspberry Pi 5 and all Raspberry Pi Zero models require a https://www.raspberrypi.com/products/camera-cable/[different camera cable].

Some cameras may come with a small piece of translucent blue plastic film covering the lens. This is only present to protect the lens during shipping. To remove it, gently peel it off.

NOTE: There is additional documentation available around fitting the recommended https://datasheets.raspberrypi.com/hq-camera/cs-mount-lens-guide.pdf[6mm] and https://datasheets.raspberrypi.com/hq-camera/c-mount-lens-guide.pdf[16mm] lens to the HQ Camera.

=== Prepare the Software

Before proceeding, we recommend ensuring that your kernel, GPU firmware and applications are all up to date. Please follow the instructions on xref:../computers/os.adoc#update-software[keeping your operating system up to date].

Then, please follow the relevant setup instructions for xref:../computers/camera_software.adoc#rpicam-apps[`rpicam-apps`], and the https://datasheets.raspberrypi.com/camera/picamera2-manual.pdf[Picamera2 Python library].

== Hardware Specification

|===
|  | Camera Module v1 | Camera Module v2 | Camera Module 3 | Camera Module 3 Wide | HQ Camera | AI Camera | GS Camera

| Net price
| $25
| $25
| $25 
| $35
| $50
| $70
| $50

| Size
| Around 25 × 24 × 9 mm
| Around 25 × 24 × 9 mm
| Around 25 × 24 × 11.5 mm
| Around 25 × 24 × 12.4 mm
| 38 × 38 × 18.4mm (excluding lens)
| 25 × 24 × 11.9mm
| 38 × 38 × 19.8mm (29.5mm with adaptor and dust cap)

| Weight
| 3g
| 3g
| 4g
| 4g
| 30.4g
| 6g
| 34g (41g with adaptor and dust cap)

| Still resolution
| 5 megapixels
| 8 megapixels
| 11.9 megapixels
| 11.9 megapixels
| 12.3 megapixels
| 12.3 megapixels
| 1.58 megapixels

| Video modes
| 1080p30, 720p60 and 640 × 480p60/90
| 1080p47, 1640 × 1232p41 and 640 × 480p206
| 2304 × 1296p56, 2304 × 1296p30 HDR, 1536 × 864p120
| 2304 × 1296p56, 2304 × 1296p30 HDR, 1536 × 864p120
| 2028 × 1080p50, 2028 × 1520p40 and 1332 × 990p120
| 2028 × 1520p30, 4056 × 3040p10
| 1456 × 1088p60

| Sensor
| OmniVision OV5647
| Sony IMX219
| Sony IMX708
| Sony IMX708
| Sony IMX477
| Sony IMX500
| Sony IMX296

| Sensor resolution
| 2592 × 1944 pixels
| 3280 × 2464 pixels
| 4608 × 2592 pixels
| 4608 × 2592 pixels
| 4056 × 3040 pixels
| 4056 × 3040 pixels
| 1456 × 1088 pixels

| Sensor image area
| 3.76 × 2.74 mm
| 3.68 × 2.76 mm (4.6 mm diagonal)
| 6.45 × 3.63mm (7.4mm diagonal)
| 6.45 × 3.63mm (7.4mm diagonal)
| 6.287mm × 4.712 mm (7.9mm diagonal)
| 6.287mm × 4.712 mm (7.9mm diagonal)
| 6.3mm diagonal

| Pixel size
| 1.4 µm × 1.4 µm
| 1.12 µm × 1.12 µm
| 1.4 µm × 1.4 µm
| 1.4 µm × 1.4 µm
| 1.55 µm × 1.55 µm
| 1.55 µm × 1.55 µm
| 3.45 µm × 3.45 µm

| Optical size
| 1/4"
| 1/4"
| 1/2.43"
| 1/2.43"
| 1/2.3"
| 1/2.3"
| 1/2.9"

| Focus
| Fixed
| Adjustable
| Motorized
| Motorized
| Adjustable
| Adjustable
| Adjustable

| Depth of field
| Approx 1 m to ∞ 
| Approx 10 cm to ∞ 
| Approx 10 cm to ∞ 
| Approx 5 cm to ∞ 
| N/A
| Approx 20 cm to ∞
| N/A

| Focal length
| 3.60 mm +/- 0.01
| 3.04 mm
| 4.74 mm
| 2.75 mmm
| Depends on lens
| 4.74 mm
| Depends on lens

| Horizontal Field of View (FoV)
| 53.50  +/- 0.13 degrees
| 62.2 degrees
| 66 degrees
| 102 degrees
| Depends on lens
| 66 ±3 degrees
| Depends on lens

| Vertical Field of View (FoV)
| 41.41 +/- 0.11 degrees
| 48.8 degrees
| 41 degrees
| 67 degrees
| Depends on lens
| 52.3 ±3 degrees
| Depends on lens

| Focal ratio (F-Stop)
| F2.9
| F2.0
| F1.8
| F2.2
| Depends on lens
| F1.79
| Depends on lens

| Maximum exposure time (seconds)
| 3.28
| 11.76
| 112
| 112
| 670.74
| 112
| 15.5 

| Lens Mount
| N/A
| N/A
| N/A 
| N/A
| C/CS- or M12-mount
| N/A
| C/CS

| NoIR version available?
| Yes
| Yes
| Yes
| Yes
| No
| No
| No
|===

NOTE: There is https://github.com/raspberrypi/libcamera/issues/43[some evidence] to suggest that the Camera Module 3 may emit RFI at a harmonic of the CSI clock rate. This RFI is in a range to interfere with GPS L1 frequencies (1575 MHz). Please see the https://github.com/raspberrypi/libcamera/issues/43[thread on Github] for details and proposed workarounds.

=== Mechanical Drawings

Available mechanical drawings;

* Camera Module 2 https://datasheets.raspberrypi.com/camera/camera-module-2-mechanical-drawing.pdf[PDF]
* Camera Module 3 https://datasheets.raspberrypi.com/camera/camera-module-3-standard-mechanical-drawing.pdf[PDF]
* Camera Module 3 Wide https://datasheets.raspberrypi.com/camera/camera-module-3-wide-mechanical-drawing.pdf[PDF]
* Camera Module 3 https://datasheets.raspberrypi.com/camera/camera-module-3-step.zip[STEP files]
* HQ Camera Module (CS-mount version) https://datasheets.raspberrypi.com/hq-camera/hq-camera-cs-mechanical-drawing.pdf[PDF]
** The CS-mount https://datasheets.raspberrypi.com/hq-camera/hq-camera-cs-lensmount-drawing.pdf[PDF]
* HQ Camera Module (M12-mount version) https://datasheets.raspberrypi.com/hq-camera/hq-camera-m12-mechanical-drawing.pdf[PDF]
* GS Camera Module 
https://datasheets.raspberrypi.com/gs-camera/gs-camera-mechanical-drawing.pdf[PDF]

NOTE: Board dimensions and mounting-hole positions for Camera Module 3 are identical to Camera Module 2. However, due to changes in the size and position of the sensor module, it is not mechanically compatible with the camera lid for the Raspberry Pi Zero Case.

=== Schematics

.Schematic of the Raspberry Pi CSI camera connector.
image:images/RPi-S5-conn.png[camera connector, width="65%"]

Other available schematics;

* Camera Module v2 https://datasheets.raspberrypi.com/camera/camera-module-2-schematics.pdf[PDF]
* Camera Module v3 https://datasheets.raspberrypi.com/camera/camera-module-3-schematics.pdf[PDF]
* HQ Camera Module https://datasheets.raspberrypi.com/hq-camera/hq-camera-schematics.pdf[PDF]


# Benewake TFMini-S Micro LiDAR

![[TFmini-S Datasheet.pdf]]
![[TFmini-S User Manual.pdf]]
