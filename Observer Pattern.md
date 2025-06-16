The **Observer Pattern** defines a one-to-many dependency between objects so that when one object changes state, all of its dependents are notified and updated automatically. It enable loosely coupled OO designs in the code-base making classes less dependent on each other.

It uses **Subject and Observer** to define relationships i.e The subject and observers define the one-to-many relationship. We have one subject, who notifies many observers when something in the subject changes. The observers are dependent on the subject—when the subject’s 
state changes, the observers are notified. 

**NOTE**: *`Design to interface not to class. It allows one to implement design partterns easily`* 

An example is Java Swing Button(Subject) and Action Listener(Observer) in the Java Swing Package

The subject and observers define the one-to-many relationship. We 
have one subject, who notifies many observers when something in the subject 
changes. The observers are dependent on the subject—when the subject’s 
state changes, the observers are notified. 
