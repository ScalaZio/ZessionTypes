# Zession Types: compile time checked protocols in Scala 3 and ZIO

Zession types allows us to specify in the type that code will follow a particular protocol.
Zession Types can
1) Check if code correctly implements a protocol at compile time.
2) Check if the Protocol has desirable behavior (eg no dead locks, no live locks, progress guarantees)
3) Check if the behavior of an external node breaks the protocol (at run time)

A typical protocol has nodes performing actions and sending msgs to each other. The nodes have roles. 
Currently we use a monadic effect type called 'Process'. However we could use ZIO, ZStream or Fiber, extended with the code for 'Process'.
The protocol checks that the right sequences of send and receive msgs and actions are performed. 
We can perform logical operations and use Match types to perform logical branches in decision tree.
We can perform some arithmetic at compile time, and use that in our logic.
If we have a two layer protocol, with the lower layer can provide an abstraction from the actual protocol used (UDP, TCP etc), handle errors, time outs, batching and broadcast, connection and node management, NAT traversal, packet counting etc.
Then the upper layer can deal with the business logic with the mechanics abstracted away. It can respond to a time out like any other msg in the protocol.
We can model an STM (or db) in terms of msg passing with a node with an STM role.
We can model generic protocols with parameters, concurrent operations, ordered and orderless, required, optional or alternative; in a composable, orthogonal and extensible way.


This is based on the work by Alceste Scala in Effpi
 <https://alcestes.github.io/effpi>

## Authors

Effpi was developed by:

  * Alceste Scalas — DTU Compute, Technical University of Denmark
    (`alcsc (at) dtu (dot) dk`)
  * Elias Benussi — Faculty Science Ltd.
    (`elias (at) faculty (dot) ai`)

The theory behind Effpi is developed in collaboration with:

  * Nobuko Yoshida — Imperial College London, UK
   (`n.yoshida (at) imperial (dot) ac (dot) uk`)
