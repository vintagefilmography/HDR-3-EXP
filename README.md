# HDR 3 Exposure Windows software for Hawkeye

This is a modified version of basic HDR app for windows.  
It produces images with 3 exposures. The first image has   
exp = normal exp - 2 * increment  
Second image has
exp =  normal exp - 1 * increment 
And the third image has  
exp = normal exposure  

Another mofification is to use a single directory for all images. Th enumbers just continue sequentially i.e.  
seq 1 exp1  
seq 2 exp2  
seq 3 exp3  
seq 4 exp1  
etc  
It should also be notes that both the low and high dir paths should be set the same for this to work.  

Note: Hawkeye board V12 or higher and MSP FW mod are required for proper HDR operation to provide two camera triggers for a single external trigger.   
This is the windows software that runs hdr on the Wolverine scanner that has the Hawkeye mod.   
The software is written in Visual Basic and it connects to the camera and waits for the image ready event.   
After the event is receied the sw stores the first image and lowers the camera exposure for the second image.   
When the second event is received it stores the second image. The process then repeats.   
The hawkeye MSP430 firmware has a mod to trigger the camera twice for each external trigger.   
To run the sw go to the  
.../bin/Release     
dir and run the HDR.exe file.   
The Device Settings window will pop up.   
Select the device and resolution as required and click OK.   
The Device Window will close and the app window will pop up.   
Select the destination directories for the hi exposure and low exposure images by clicking on the ImgPath1 and ImgPath2 buttons.   
For this 3 exposure build both paths should be the same.  
Then click on Trigger buton a few times. It will go from red to white.  
Leave it white for free run.   
Click Start.   
The camera preview will be displayed in the preview window.   
Click on ZoomIn and ZoomOut buttons and set the zoom as needed.   
Click on Settings button.   
The familiar camera settings will pop up.   
Set the color, partial scan etc Make sure the auto reference on the exposure tab is set higher that 84.   
Around 100 is a good setting which gives overexposed image.   
Click on OK.   
The window will close.   
Click on Start button.   
It should go white.   
Click on SaveConf button to save the device settings.   
Make sure the Start buttoon is not active, otherwise an exception will pop up.   
The next time when you run the app you can use the LoadConf to retrieve the settings.   
The settings are stored in device_state.txt file in the same directory where the app resides.   
Select the bit depth by clicking the Bit64 button.   
The Bit64 button will turn red indicating 64 bit mode.   
Make sure that the Start button is not active when you are doing this otherwise the app will crash.   
Essentially the start botton starts the live display and the bit depth and soem other camera critical settings can not be changed in Live mode.   
Most of other settings can be changed in Live mode however.   
The SaveTiff button also can be set in Live mode.   
If active it will switch from default Jpeg format to Tiff.   
Set exposure increment by typing in the number in teh Exp Inc bnumber box.   
The up and down arrows also work.  
The final exposure value can be double checked by clicking the ShowExp button.   
It is to be notes that the EXP value is 10 times lower than teh value shown in the box. 
Around 30 seems to work good which is actually equal to 3.   
Click on Trigger button to activate external trigger.   
Click on ImgSave.   
It should turn red.(Keep an eye on this button when testing. It could flood your drive with images if trigger is left on FreeRun).   
Click on Start Button. The app is now ready for images.   
Run the scanner.   
All images will be stored in the same dir. The numbers will go sequentially.  
So, for 3 exposures it will go  
img1  exp1  
img2  exp2 
img3  exp3  
img4  exp1  
img5  exp2  
etc  

Note, once the scan process is complete you can use an app to run the high and low images.   
The app that seems to work very can be obtained from the following site:   
http://enblend.sourceforge.net/   
Download enfuse and use the enfuse-hdr.bat (included here in the repository) script to run combine the images.
