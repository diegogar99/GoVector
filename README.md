GoVector
========

A ShiViz compatible Logging Library in Go

This is small library you can add to any Go project to create a ShiViz Compatible Log. 

Files Included:

Govec Folder : Contains the Library and all its dependencies 
TestFile : A small program to Test the Library 
exampleprocess-log : An example log generated by library
Experimental Development Folder : A folder containing code used in development of this library and is of no consequence to the user

API Info

The Library Supports 3 Major Calls
Initialize()
PrepareSend()
UnpackReceive()
The calls are explained below

How to Use This Library

Step 0
To Use This Library, copy the govec folder in your project. In your program, import it by adding this :
	"./govec"
to your import list.
	
Step 1:
Create a Global Variable and Initialize it using like this = 

	Logger:= Initialize("MyProcessName",ShouldYouSeeLoggingOnScreen,ShouldISendVectorClockonWire,Debug)
	
ShouldYouSeeLoggingOnScreen prints whatever is logged by the Library on Standard Output
ShouldISendVectorClockonWire should be true if all involved Networked Program are also using this library and false if
only you are logging 
Debug prints extra information on Standard Output
	
Step 2:
When Ever You Decide to Send any []byte, call PrepareSend and send output. 
So instead of:

	connection.Send([]YourMessage)
call :

	connection.Send(PrepareSend("Message Description", []YourMessage))

Step 3:
When Receiveing a []byte Message, Unpack it with UnpackRecieve Call. 
So after you call :

	connection.Receive([]RecievedBuffer)
call :
	
	[]UnpackedMessage :=  UnpackReceive("Message Description", []ReceivedBuffer)
using UnpackedMessage for further processing. Note You may have to convert an Array into a slice for ReceivedBuffer
	
	
