# RPS-2-Python

import random

#this player uses history to try to predict the opponents
#next move.

#Remember the input variable is given to us with our opponents
#last move. We will find the last time they made the same throw,
#and then throw what will beat whatever they threw next.

#Example.  Input = "R" - our opponent just threw "R"
#			We will look  through the history(oldThrows)
#			For the last time they threw "R". Then we will
#			look at what they threw next, and throw to beat that.

#Example 2. Suppose After a few rounds oldThrows =[ "R", "R", ,"P", "S", "S", "R"]
#			Then in the next round, we get input="P"
#			So we will look through oldThrows to get the largest index of "P"
#   		Then look at the move after that, "S" in this case. 
#			We will throw "R", since that beats "S".
#			The idea is that since the opponent threw "S" after paper last time,
#			maybe they will do it again.

#We still store our opponents moves in oldThrows 


#in the first round input is empty!
if not input:
	#so initialize the list, and pick a random throw
	oldThrows = []
	output = random.choice(["R","P", "S"])

#for every turn but the first we go here	
else:
	
	lastIndex = getLastIndexOf(oldThrows, input)

	if(lastIndex == -1):
		output = random.choice(["R","P", "S"])

	else:
		throwToBeat = ""
		if lastIndex < (len(oldThrows)-1):
			throwToBeat = oldThrows[lastIndex +1]
		else: 
			throwToBeat = input
		output = throwThatBeatsThis(throwToBeat)
		
oldThrows.append(input)

#gets the last index of item in array
def getLastIndexOf(array, item):
	for i in range(len(array)-1, -1, -1):
		if item == array[i]:
			return i
	return -1
#end of getLastIndexOf

#returns the throw that will beat throwToBeat
def throwThatBeatsThis(throwToBeat):
	if throwToBeat == "R":
		return "P"
	elif throwToBeat == "S":
		return "R"
	elif throwToBeat == "P":
		return "S"
	#theres a bunch of lines to write here
#end throwThatBeatsThis

