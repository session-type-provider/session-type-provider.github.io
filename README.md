# Session Type Providers (STP)
[STP](https://github.com/rumineykova/Sast) is a type provider in F# that generates APIs from protocol specifications. 

Consider the following protocol, between a client and a server. The protocol below specifies that a client sends a message tagged as DIV (stands for dicision), containing two payloads. Then the Server replied with a message RES with one integer payload. 
### Scribble protocol:
```
DIV(x:int, y:int) from C to S; 
RES(z:int) from S to C; 
```

### F# program 
```
s = STP<"Protocol.scr", C>
let z = Buf<int>()
s.send(S, Div, 4, 2).receive(S, Res, z)
'''

# Support for interaction refinements
The tool supports checks of payload constraints. For example, we can augment the protocol below to specify that teh second argument is not zero. 
```
DIV(x:int, y:int) from C to S; @{y!=0}  
RES(z:int) from S to C; @{z=x/y}
```
Then the geenrated code for sending will explicitly contain teh specified check. 

# Publications
CC'18: Session type Provider: Compile-time API Generation for Distributed Protocols with Interaction Refinements in F#
You can find the full version of the paper [here] (https://www.doc.ic.ac.uk/~rn710/thesis/stp.pdf)

# You can the slides from the presentation [here](https://github.com/rumineykova/Sast) 

# Check the tool [here](https://github.com/rumineykova/Sast)



