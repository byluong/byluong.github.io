---
title: "Are DFAs Turing Recognizable?"
header:
  teaser: assets/images/turing.PNG
---
(hint: yes). Simulating DFAs using multi-tape turing machines.  

[simulator](http://web.cs.ucdavis.edu/~doty/automata/tm.html)  

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

## 4-tape TM simulation of two-input alphabet DFAs:
```
states:          q0,q1,q2,q3,q4,q5,q6,q7,q8,q9,q10,q11,q12,q13,q14,q15,q16,q17,q18,q19,q20,q100,q101,q102,q103,q104,qA,qR
input_alphabet:  0,1,2,3,a,b,:,|,$
tape_alphabet:   0,1,2,3,a,b,x,:,|,$,_
start_state:     q0
accept_state:    qA
reject_state:    qR
delta:           q0,$___ -> q1,$$$$,RRRR
                q1,?___ -> q100,?___,RSSS
                q100,|___ -> q2,|___,RSSS

                #match LHS a 
                q2,0___ -> q2,00__,RRSS
                q2,1___ -> q2,11__,RRSS
                q2,2___ -> q2,22__,RRSS
                q2,3___ -> q2,33__,RRSS
                q2,a___ -> q2,aa__,RRSS
                q2,???? -> q3,????,SSSS

                #RHS a
                q3,0___ -> q3,00__,RRSS
                q3,1___ -> q3,11__,RRSS
                q3,2___ -> q3,22__,RRSS
                q3,3___ -> q3,33__,RRSS
                q3,:___ -> q4,::__,RRSS
...
                #end of input, write final state onto end of fourth tape
                q9,000_ -> q18,0000,RLLR
                q9,100_ -> q18,1001,RLLR
                q9,200_ -> q18,2002,RLLR
                q9,300_ -> q18,3003,RLLR

                #check for accept state
                #go right on first tape
                q18,???? -> q18,????,RSSS
                q18,x$$_ -> q19,x$$_,LSSS
                q19,|$$_ -> q20,|$$_,LSSL

                #proceed left on 0,1,2,3,:
                q20,?$$? -> q20,?$$?,LSSS

                #accept if match found
                q20,0$$0 -> qA,0$$0,SSSS
                q20,1$$1 -> qA,0$$0,SSSS
                q20,2$$2 -> qA,0$$0,SSSS
                q20,3$$3 -> qA,0$$0,SSSS

                #reject if | on other side reached
                q20,|$$0 -> qR,|$$0,SSSS
                q20,|$$1 -> qR,|$$1,SSSS
                q20,|$$2 -> qR,|$$2,SSSS
                q20,|$$3 -> qR,|$$3,SSSS
```
Full source available on request.