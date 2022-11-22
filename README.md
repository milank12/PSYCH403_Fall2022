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
#=====================
#START EXPERIMENT
#=====================
my_text.text = start_msg
my_text.draw()  #-present start message text
win.flip() 
event.waitKeys() #-allow participant to begin experiment with button press

blockTimer = core.Clock()
trialTimer = core.Clock()
stimTimer = core.Clock()
respTimer = core.Clock()
#=====================
#BLOCK SEQUENCE
#=====================
for block in range (nBlocks): #-for loop for nBlocks
    blockTimer.reset()
    blockStart = blockTimer.getTime()
    
    my_text.text = block_msg #-present block start message
    my_text.draw()
    win.flip()
    event.waitKeys()
    np.random.shuffle(stims) #-randomize order of trials here
    #-reset response time clock here
    
    #=====================
    #TRIAL SEQUENCE
    #=====================    
    for trial in range (nTrials):  #-for loop for nTrials *
        trialTimer.reset()
        trialStart = trialTimer.getTime()
    
        my_image.image = os.path.join(image_dir,stims[trial])
        
        stimTimer.reset()
        while stimTimer() <= 1:
            fix_text.draw() 
            win.flip() 
            core.wait(.5)
        
        stimTimer.reset()
        respTimer.reset()
        while stimTimer() <= .5:
            my_image.draw()
            win.flip()
            core.wait(1)
        
        stimTimer.reset()
        while stimTimer() <= 1:
            fix_text.draw() 
            win.flip() 
            core.wait(.5)
        
        event.waitKeys(0)
        RTrespTimer.getTime()
        
        trialEnd = trialTimer.getTime()
    
    blockEnd = blockTimer.getTime()

Frame-based Timing Exercises:

1.
mon = monitors.Monitor('myMonitor', width=36.83, distance=60)
mon.setSizePix([2560,1440])

win = visual.Window(monitor=mon, size=(200,200), color=[-1,-1,-1], units = "height")
start_msg = "Welcome to my experiment!" #-define experiment start text unsing psychopy functions
block_msg = "Press any key to continue to the next block." #-define block (start)/end text using psychopy functions
end_trial_msg = "End of block."

my_text = visual.TextStim(win)
my_image = visual.ImageStim(win) 
fix_text = visual.TextStim(win, text='+')#-define stimuli using psychopy functions
#set durations
fix_dur = 0.2 #200 ms
image_dur = 0.1 #100 ms
text_dur = 0.2 #200 ms

refresh=1.0/60.0
#set frame counts
fix_frames = int(fix_dur / refresh) #whole number
image_frames = int(image_dur / refresh) #whole number
text_frames = int(text_dur / refresh) #whole number
#the total number of frames to be presented on a trial
total_frames = int(fix_frames + image_frames + text_frames)
#-create response time clock
#-make mouse pointer invisible

#=====================
#START EXPERIMENT
#=====================
my_text.text = start_msg
my_text.draw()  #-present start message text
win.flip() 
event.waitKeys() #-allow participant to begin experiment with button press

#blockTimer = core.Clock()
#trialTimer = core.Clock()
#stimTimer = core.Clock()
#respTimer = core.Clock()
#=====================
#BLOCK SEQUENCE
#=====================
for block in range (nBlocks): #-for loop for nBlocks
    #blockTimer.reset()
    #blockStart = blockTimer.getTime()
    
    my_text.text = block_msg #-present block start message
    my_text.draw()
    win.flip()
    event.waitKeys()
    np.random.shuffle(stims) #-randomize order of trials here
    #-reset response time clock here
    
    #=====================
    #TRIAL SEQUENCE
    #=====================    
    for trial in range (nTrials):  #-for loop for nTrials *
        #trialTimer.reset()
        #trialStart = trialTimer.getTime()
    
        my_image.image = os.path.join(image_dir,stims[trial])
        
        #stimTimer.reset()
        #while stimTimer() <= 1:
        for frameN in range(total_frames):
            
            if 0 <= frameN <= fix_frames:
                fix_text.draw() 
                win.flip() 
                #core.wait(.5)
                if frameN == fix_frames: #last frame for the fixation
                    print("End fix frame =", frameN) #print frame number
        
        #stimTimer.reset()
        #respTimer.reset()
        #while stimTimer() <= .5:
            if fix_frames < frameN <= fix_frames + (fix_frames+image_frames):
                my_image.draw()
                win.flip()
                if frameN == (fix_frames+image_frames): #last frame for the image
                    print("End image frame =", frameN) #print frame number  
            #core.wait(1)
        
        #stimTimer.reset()
        #while stimTimer() <= 1:
            if (fix_frames+image_frames) < frameN < total_frames:
                if frameN == (fix_frames+image_frames) + 1:
                    fix_text.draw() 
                    win.flip() 
                    if frameN == (total_frames-1): #last frame for the text
                        print("End text frame =", frameN) #print frame number  
                #core.wait(.5)
        #print("Image Duration was {} seconds".format(imgEndTime - imgStartTime))
                
win.close()                

2. After adding in the code to montior dropped frames, I can see that I'm dropping 60 frames during the experiment, or 3 per trial. In this case, I'll switch back to the clock method.
