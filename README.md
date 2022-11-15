This is my set of answers to Assignment 6:

Dialog Box Exercises:
1 and 2:
from psychopy import gui

my_dlg = gui.Dlg(title="my experiment")
my_dlg.addFixedField('session:',1)
my_dlg.addText('exp_info')
my_dlg.addField('age:',0)
my_dlg.addField('gender:')
my_dlg.addField('handedness:', choices=['right', 'left'])
my_dlg.addField('subject_nr:',0)
show_dlg = my_dlg.show() 
   
Using DlgFromDict:

subject_info = {'session':1,'subject_nr':0, 'age':0, 'gender':('male','female','other','prefer not to say'), 'handedness':('right','left','ambi')}

from psychopy import gui
print("All variables have been created! Now ready to show dialog box!")
print(subject_info)
my_dlg = gui.DlgFromDict(dictionary=subject_info, title = "subject info", fixed = "session")


5.
from psychopy import gui

my_dlg = gui.Dlg(title="my experiment")
my_dlg.addField('age:',0)
my_dlg.addField('gender:')
my_dlg.addField('handedness:', choices=['right', 'left'])
my_dlg.addField('subject_nr:',0)
show_dlg = my_dlg.show() 

from datetime import datetime

date = datetime.now()
print(date)

filename = str(exp_info['subject_nr']) + '_' + exp_info['date'] + '.csv'
print(filename)

main_dir = os.getcwd() 
sub_dir = os.path.join(main_dir,'sub_info',filename)

Monitor and Window Exercises:
1. Using different units for the monitor size will affect the size of the window and the stimuli created and how they are diplayed on the screen. For example, the height unit will make everything fit corresponding to the height of the window while keeping the stimuli square, while centimeters will set the size and location of the stimuli based on the given centimetres for the size of the screen.
2. Changing the colour space values will change the lightness of colour present in the window, on a scale of -1 to 1, with -1 being dark (black) and 1 being full opacity. (-1, 1, -1) gives a fully green screen, (1, -1, 1) gives magenta, (0, -1, -1) will give dark red.
3.
from psychopy import visual, monitors

mon = monitors.Monitor('myMonitor', width=36.83, distance=60)
mon.setSizePix([2560,1440])

win = visual.Window(monitor=mon, size=(200,200), color=[-1,-1,-1], units = "height")

Stimulus Exercises:
1. from psychopy import visual, monitors, event

mon = monitors.Monitor('myMonitor', width=36.83, distance=60)
mon.setSizePix([2560,1440])

win = visual.Window(monitor=mon, size=(400,400), color=[-1,-1,-1])
import os
os.chdir('/Users/milankalra/Documents') 
main_dir = os.getcwd() 
image_dir = os.path.join(main_dir,'images') 

pic_loc = os.path.join(image_dir,'face01.jpg')

my_image = visual.ImageStim(win, image=pic_loc,size=1)) 

my_image.draw()
win.flip()
event.waitKeys()
win.close()

When using a 400 x 400 window, the image is cut off on the ends because of the aspect ratio not matching the window. If you use the size paramater in ImageStim, you can change the aspect ratio and make it wider by using "size+=(0.5,-0.5)"


3. fix_text = visual.TextStim(win, text='+')
4. 
start_msg = "Welcome to my experiment!"
block_msg = "Press any key to continue to the next block."
end_trial_msg = "End of block."

my_text = visual.TextStim(win)
my_image = visual.ImageStim(win)

my_text.text = start_msg
my_text.draw()
win.flip() 
event.waitKeys() 

for block in range (nBlocks):
    my_text.text = block_msg
    my_image.draw()
    win.flip()
    event.waitKeys()
    
    for trial in range (nTrials):
      my_image.image = os.path.join(image_dir,stims[trial])
      my_image.draw() 
      fix_text.draw() 
      win.flip() 
      event.waitKeys()   
        
win.close()        
