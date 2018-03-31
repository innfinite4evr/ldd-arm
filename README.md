# ldd-arm
search for shared objects or needed .so librariers which helps in finding dependencies of blobs
I FOUND THIS IS ON RUSSIAN FORUMS .
I DONT HOLD CREDIT FOR THIS

A small TUTORIAL (on request) to find the missing lib (.so) when creating a device tree Android.
It's not the first time I've come across that people are looking for the missing shared lib at random, sorting everything out. In fact, there is a more or less automatic way (advanced developers do not need this manual).

In the screenshot you can see that I pulled all the dependencies camera.msm8937.so from the proprietary one by one command. Of course, do not take all the received from the stock firmware and immediately gladly transfer to your assembly. You just see all the dependencies.

How to implement:
In the Linux terminal, we create our executable ldd-arm which will then pull dependencies:

echo 'readelf -d $1 | grep "\(NEEDED\)" | sed -r "s/.*\[(.*)\]/\1/" '| sudo tee -a /usr/local/bin/ldd-arm

We issue the executable rights: 
 
sudo chmod +x /usr/local/bin/ldd-arm

Done! Now you can use if from anywhere !
Enter in the terminal 

ldd-arm camera.msm8937.so

Output:

libcamera_client.so
liblog.so
libhardware.so
libutils.so
libcutils.so
libdl.so
libsync.so
libgui.so
libmmcamera_interface.so
libmmjpeg_interface.so
libui.so
libcamera_metadata.so
libqdMetaData.so
libqservice.so
libbinder.so
libcam.meiyan.so
libarcsoft_low_light_shot.so
libmpbase.so
libcam_lowlight.so
libarcsoft_high_dynamic_range.so
libc++.so
libc.so
libm.so
