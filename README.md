
**This is my set of answers to Assignment 3:**

Conditionals Exercises:

1)

    response = '1'
    
    if response == "1" or response == '2':
        print("OK")
        
    elif response == "NaN":
        print("subject did not respond")
        
    else: print("subject pressed the wrong key")

2)

    response = '1'
    
    if response == "1" or response == '2':
        print("OK")
        if response == "1":
            print("Correct!")
        if response == "2":
            print("Incorrect!")
        
 3) The script does what it's supposed to for the most part. For the responses of 1 and 2, we get the ouput "OK" along with the corresponding accuracy message. For any other response, we get the wrong key message. However, for when response is not filled, or the scenario where the subject did not respond, we still get the subject pressed the wrong key message. The response needs to be specifically NaN for the no response message to run (if the system we are using to run the study codes a non-response as "NaN" this works fine).
 
 For Loop Exercises:
 
 1)

    letter = ["M", "I", "L", "A", "N"]
    
    for i in letter:
        name = i
        print(name)

2) 

    letter = ["M", "I", "L", "A", "N"]
    
    count = -1
    
    for i in letter:
        count = count+1
        
        name = i
        print(name)
        print("Letter %i" %count)
        

3)

    names = ["Amy", "Rory", "River"]
    
    for name in names: #loops through names
        print(name)
        
        for letter in name: #loops through letters
            print(letter)
        
4) 

    names = ["Amy", "Rory", "River"]
    
    
    for name in names: #loops through names
        
        print(name)
        count = 0
        
        for letter in name: #loops through letter
            print(letter)
            print("Letter %i" %count)
            count = count + 1
        


While Loop Exercises:

1) 

    iteration = 0
    
    while iteration < 10:
        print("image1.png")
        iteration = iteration + 1
       
        if iteration == 10:
            iteration  = iteration + 1
            break
    
    while iteration > 10:
        print("image2.png")
        iteration = iteration + 1
        
        if iteration == 21:
            break
            

2) 

    import random
    
    response = False
    iteration = 0
    
    while not response:
        iteration = iteration + 1
        print("showing an image for %i iterations" %iteration)
        
        if random.randint(0,20) == 1 or random.randint(0,10) == 2:
            response = True
        

3) 

    import random
    
    response = False
    iteration = 0
    
    failsafe = -1
    
    while not response:
        
        failsafe  = failsafe +1 
        if failsafe == 5:
            break
        
        iteration = iteration + 1
        print("showing an image for %i iterations" %iteration)
        
        if random.randint(0,20) == 1 or random.randint(0,10) == 2:
            response = True


 
 
