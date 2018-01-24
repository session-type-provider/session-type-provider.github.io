# Session Type Providers (STP)
[STP] (https://github.com/rumineykova/Sast) is a compiler plug-in in F# that generated APIs from protocols. 

Consider the following protocol between a client and a server
####Scribble protocol:
```
DIV(x:int, y:int) from C to S; 
RES(z:int) from S to C; 
```
####F# program 

# Support for interaction refinements
```
DIV(x:int, y:int) from C to S; @{y!=0}  
RES(z:int) from S to C; @{z=x/y}
```

# Solution

# Publications
CC'18: Session type Provider: Compile-time API Generation for Distributed Protocols with Interaction Refinements in F#
You can find the full version of the paper here: https://www.doc.ic.ac.uk/~rn710/thesis/stp.pdf


