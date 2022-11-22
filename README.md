This is my set of answers to Assignment 7:

Wait Exercises:
 for trial in range (nTrials):  #-for loop for nTrials *
        my_image.image = os.path.join(image_dir,stims[trial])
        
        fix_text.draw() 
        win.flip() 
        core.wait(.5)
        
        my_image.draw()
        win.flip()
        core.wait(1)
        
        my_text.text = end_trial_msg
        my_text.draw()
        win.flip()
        core.wait(.5)
        
Clock Exercises:
1. 
import os
#stuff you only have to define once at the top of your script
main_dir = os.getcwd() 
image_dir = os.path.join(main_dir,'images')

my_image = visual.ImageStim(win)
fix_text = visual.TextStim(win, text='+')

stims = ['face01.jpg','face02.jpg','face03.jpg'] #create a list if images to show
nTrials=3 #create a number of trials for your images
wait_timer = core.Clock

for trial in range(nTrials): #loop through trials
    
    my_image.image = os.path.join(image_dir,stims[trial])
    
    fix_text.draw()
    win.flip()
    core.wait(.5)
    
    my_image.draw()
    win.flip()
    imgStartTime = wait_timer().getTime()
    core.wait(2)
    imgEndTime = wait_timer().getTime()
    
    fix_text.draw()
    win.flip()
    core.wait(.5)
    
    print("Image Duration was {} seconds".format(imgEndTime - imgStartTime))
    
win.close() #close the window after trials have looped    

Here are the results:
Image Duration was 1.3257988030090928e-05 seconds
Image Duration was -1.2500095181167126e-07 seconds
Image Duration was 2.5003100745379925e-07 seconds

Clearly core.wait is not very accurate. My output values also changed after stopping other programs on my computer, which suggests that I'm dropping frames.

2. 
stims = ['face01.jpg','face02.jpg','face03.jpg'] #create a list if images to show
nTrials=3 #create a number of trials for your images
waitTimer = core.Clock()
stimTimer = core.Clock()

for trial in range(nTrials): #loop through trials
    
    my_image.image = os.path.join(image_dir,stims[trial])
    
    fix_text.draw()
    win.flip()
    core.wait(.5)
    
    stimTimer.reset()
    imgStartTime = waitTimer.getTime()
    while stimTimer.getTime() <= 2:
            my_image.draw()
            win.flip()
    imgEndTime = waitTimer.getTime()
    
    fix_text.draw()
    win.flip()
    core.wait(.5)
    
    print("Image Duration was {} seconds".format(imgEndTime - imgStartTime))
    
win.close() #close the window after trials have looped    

Here are the results:
Image Duration was 2.0090473489835858 seconds
Image Duration was 2.0056376599823125 seconds
Image Duration was 2.0048596400010865 seconds

This seems to be much more accurate, seemingly accurate to about 2 decimal places.

3. 
stims = ['face01.jpg','face02.jpg','face03.jpg'] #create a list if images to show
nTrials=3 #create a number of trials for your images
waitTimer = core.Clock()
stimTimer = core.CountdownTimer()

for trial in range(nTrials): #loop through trials
    
    my_image.image = os.path.join(image_dir,stims[trial])
    
    fix_text.draw()
    win.flip()
    core.wait(.5)
    
    stimTimer.reset()
    stimTimer.addTime(1)
    imgStartTime = waitTimer.getTime()
    while stimTimer.getTime() > 2:
            my_image.draw()
            win.flip()
    imgEndTime = waitTimer.getTime()
    
    fix_text.draw()
    win.flip()
    core.wait(.5)
    
    print("Image Duration was {} seconds".format(imgEndTime - imgStartTime))
    
win.close() #close the window after trials have looped    

Here are the results:
Image Duration was 4.537985660135746e-06 seconds
Image Duration was 4.317989805713296e-06 seconds
Image Duration was 4.089990397915244e-06 seconds

This method doesn't seem very accurate, with comparable results to core.wait. This could be down to slowdown on my machine.


4.


