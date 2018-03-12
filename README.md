# Session Type Providers (STP)
[STP](https://github.com/rumineykova/Sast) is a type provider in F# that generates APIs from protocol specifications. 

Consider the following protocol, between a client and a server. The protocol below specifies that a client sends a message tagged as DIV (stands for division operation), containing two payloads. Then the Server replies with a message RES (stands for result) with one integer payload. 
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
```

# Support for interaction refinements
The tool supports also checks of payload constraints. For example, we can augment the protocol below to specify that the second argument of a divition cannot be zero. 
```
DIV(x:int, y:int) from C to S; @{y!=0}  
RES(z:int) from S to C; 
```
Then the geenrated code for sending will explicitly contain the specified check. 

# Publications
CC'18: [Session type Provider: Compile-time API Generation for Distributed Protocols with Interaction Refinements in F#](http://mrg.doc.ic.ac.uk/publications/a-session-type-provider/paper.pdf)

# Resources: 
- [Slides from the presentation at CC'18](http://mrg.doc.ic.ac.uk/publications/a-session-type-provider/slides.pdf) 
- [Check the tool](https://github.com/rumineykova/Sast)



