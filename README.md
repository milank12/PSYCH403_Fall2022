This is my set of answers to Assignment 3:

Experiment Structure Exercises:
 #=====================
#IMPORT MODULES
#=====================
import numpy as n #-import numpy and/or numpy functions *

#STIMULUS AND TRIAL SETTINGS
#=====================
nTrials = 10
nBlocks = 2 #-number of trials and blocks *
stims = ["face.01.jpg", "face02.jpg", "face03.npg", "face04.jpg", "face05.jpg", "face06.jpg", "face07.jpg", "face08.jpg", "face09.jpg", "face10.jpg"] #-stimulus names (and stimulus extensions, if images) *
height = 200
width - 200
orientation = center
time = 1 #-stimulus properties like size, orientation, location, duration *
startmessage = ("Please press enter to begin") #-start message text *

#=====================
#PREPARE DATA COLLECTION LISTS
#=====================
correct_responses = []#-create an empty list for correct responses (e.g., "on this trial, a response of X is 
    #correct") *
part_responses = []#-create an empty list for participant responses (e.g., "on this trial, response was a 
    #X") *
response_accuracy = []#-create an empty list for response accuracy collection (e.g., "was participant 
    #correct?") *
response_times = []#-create an empty list for response time collection *
response_orders = []#-create an empty list for recording the order of stimulus identities *
stim_order = []#-create an empty list for recording the order of stimulus properties *

#=====================
#BLOCK SEQUENCE
#=====================
for block in nBlocks: #-for loop for nBlocks *
    #-present block start message
   np.random.shuffle(stims) #-randomize order of trials here *
    #-reset response time clock here
    
#=====================
#TRIAL SEQUENCE
#=====================    
for trial in nTrials: #-for loop for nTrials *
        #-set stimuli and stimulus properties for the current trial
        #-empty keypresses
        
  Import Exercises: 
   #=====================
#IMPORT MODULES
#=====================
import numpy as n #-import numpy and/or numpy functions *
from psychopy import core, gui, visual, event #-import psychopy functions
import json #-import file save functions
import os #-(import other functions as necessary: os...)


Directory Exercises:
1.
pics = []
for i in range(1,10):
    pics.append("cat" + str(i) + ".jpg")

2.
for image in pics:
    if ims_in_dir == image:
        print (image + "was found!")
    
    if not image == ims_in_dir:
       raise Exception("The image lists do not match up!")
3. 
#PATH SETTINGS
#=====================
main_dir = os.getcwd()#-define the main directory where you will keep all of your experiment files
save_path = "/Users/milankalra/Documents"#-define the directory where you will save your data
image_dir = os.path.join(main_dir, "images")#-if you will be presenting images, define the image directory
os.path.isdir(main_dir)
os.path.isdir(image_dir)#-check that these directories exist
        

