This is my set of answers to Assignment 2:

Variable Operations Exercises:
1) Only the string form of subnr works because we are combining two variables of the same type, whereas with subnr_int we are combining a string and an integer.
2) print(sub_code + (" ") + sub_nrstr)
print(sub_code + (" ") + (sub_nrstr)*3)
print((sub_code + sub_nrstr)*3)
print((sub_code)*3 + (sub_nrstr)*3)

List Operations Exercises:
1)numlist = [1, 2, 3]

print((numlist)*2)

2)import numpy as np

numarr = np.array([1, 2, 3])
print((numarr)*2)

When we multiply an array by 2, the integers within the array are each multiplied individually, whereas when we multiply a list, the list itself is doubled as a whole.

3) strlist = ["do"*2, "re"*2, "mi"*2, "fa"*2]
strlistarr = np.array(strlist)
print((strlistarr))

strlist = [["do"]*2, ["re"]*2, ["mi"]*2, ["fa"]*2]
strlistarr = np.array(strlist)
print((strlistarr))


Zipping Exercise: 

houses = ["house1.png", "house2.png", "house3.png", "house4.png", "house5.png"]
faces = ["face1.png", "face2.png", "face3.png", "face4.png", "face5.png"]
cues = ["cue1", "cue2"]

houses_extend = houses*5
faces_extend = list(np.repeat(faces,5))



pairing1 = list(zip(houses_extend, faces_extend, ["cue1"]*25))
pairing1_cb = list(zip(faces_extend, houses_extend, ["cue1"]*25))
pairing2 = list(zip(houses_extend, faces_extend, ["cue2"]*25))
pairing2_cb = list(zip(faces_extend, houses_extend, ["cue2"]*25))

finalexp = pairing1 + pairing1_cb + pairing2 + pairing2_cb


import numpy as np
numpy_exp = np.array(finalexp)
np.random.shuffle(numpy_exp)
print(numpy_exp)


Indexing Exercises:
1)colours = ["red", "orange", "yellow", "green", "blue", "purple"]
2)print(colours[4])
3)print(colours[4][2] + colours[4][3]) 
4)colours.remove("purple")
colours.insert(5,"violet")
colours.insert(6,"indigo")

print(colours)

Slicing Exercises:
1)list100 = (range(101))
print(list(list100))

2)print(list(list100[:11]))

3)print(list(list100[::-2]))

4)print(list(list100[101:96:-1]))

5)print(list(list100[40:44:1]) == [39, 40, 41, 42, 43])

They are not the same (false)
