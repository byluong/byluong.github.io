---
title: "ECS 120: Theory of Computation"
---
## Here's some code:

```
states: q1,qA,qR
input_alphabet:  a,b,c,d,e,f
tape_alphabet:   a,b,c,d,e,f,0,_
start_state:     q1
accept_state:    qA
reject_state:    qR
delta:           q1,?_ -> q1,?_,RS
                 q1,a_ -> q1,a0,RR
                 q1,__ -> qA,__,SS
```

This TM counts the number of a's on the first tape and writes that number of 0's on the second tape. It demonstrates the use of the ? wildcard in specifying transition rules.