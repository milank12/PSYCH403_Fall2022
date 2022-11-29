**This is my set of answers to Assignment 8:**

Psychopy Keypress Exercises:
1. 

    if keys: #if there are keypresses stored in keys
        sub_resp = keys[0] #only count the first keypress
        

This code will ensure only the first keypress in each trial is recorded.

2. 
If the "if yes:" statemtent is unindented, we no longer get a 

Recording Data exercises:

1, 

    my_dict = {'key_name':key_names, 'reaction_times':subject_RT, 'accuracy':sub_acc, 'correct_responses':corr_resp}

     data_as_dict = []
        for a,b,c,d in zip(key_name[block], subject_RT[block], sub_acc[block], corr_resp[block]):
            data_as_dict.append({'key_name':a,'subject_RT':b,'sub_acc':c,'corr_resp':d})
            
        print(data_as_dict)        

2.

    for block in range(nBlocks):
        for trial in range(nTrials):
            prob[block][trial] = prob_sol[np.random.choice(4)]
            corr_resp[block][trial] = prob[block][trial][1]
            
            rt_clock.reset()  # reset timing for every trial
            cd_timer.add(3) #add 3 seconds
    
            event.clearEvents(eventType='keyboard')  # reset keys for every trial
            
            count=-1 #for counting keys
            while cd_timer.getTime() > 0: #for 3 seconds
    
                my_text.text = prob[block][trial][0] #present the problem for that trial
                my_text.draw()
                win.flip()
    
                #collect keypresses after first flip
                keys = event.getKeys(keyList=['1','2','3','4','escape'])
    
                if keys:
                    count=count+1 #count up the number of times a key is pressed
    
                    if count == 0: #if this is the first time a key is pressed
                        #get RT for first response in that loop
                        resp_time[block][trial] = rt_clock.getTime()
                        #get key for only the first response in that loop
                        sub_resp[block][trial] = keys[0] #remove from list
    
            #record subject accuracy
            #correct- remembers keys are saved as strings
            if sub_resp[block][trial] == str(corr_resp[block][trial]):
                sub_acc[block][trial] = 1 #arbitrary number for accurate response
            #incorrect- remember keys are saved as strings              
            elif sub_resp[block][trial] != str(corr_resp[block][trial]):
                sub_acc[block][trial] = 0 #arbitrary number for inaccurate response 
                                        #(should be something other than -1 to distinguish 
                                        #from non-responses)
                        
            #print results
            print('problem=', prob[block][trial], 'correct response=', 
                  corr_resp[block][trial], 'subject response=',sub_resp[block][trial], 
                  'subject accuracy=',sub_acc[block][trial], 'reaction time=',
                  resp_time[block][trial])
    
    win.close()
    
    data_as_list = [prob, corr_resp, sub_resp, sub_acc, resp_time]
    print(data_as_list)

Save CSV Exercises:

    with open(fullAddress, 'w') as sub_data:
        fieldnames = ['block', 'trial', 'problem','corr_resp','sub_resp','sub_acc', 'resp_time']
        data_writer = csv.DictWriter(sub_data, fieldnames=fieldnames)
        data_writer.writeheader()
    
        for block in range(nBlocks):
            data_as_dict = []
            for a,b,c,d,e,f,g in zip(blocks[block], trials[block], prob[block], corr_resp[block], sub_resp[block], sub_acc[block], resp_time[block]):
                data_as_dict.append({'block':a, 'trial':b, 'problem':c,'corr_resp':d,'sub_resp':e,'sub_acc':f, 'resp_time':g})
            print(data_as_dict)
            for iTrial in range(nTrials):
                data_writer.writerow(data_as_dict[iTrial])
                
            
 Load CSV Exercises:
 1. 

    df=pd.read_csv(fullPathofCSVFilesAString)
    print(df)

2.

    df=pd.read_csv(fullPathofCSVFilesAString)
    acc_trials = df.loc[df['sub_acc'] == 1] #show only trials on which subject was correct
    print(acc_trials)
