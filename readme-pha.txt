[This is the original README from David Poole's implementation - S.A.]

This directory contains an implementation of Probabilistic Horn abduction.

The implementation is written in Prolog. It has been tested with both Sicstus
Prolog and Quintus Prolog. It should be very portable.

To run the program, in Prolog, do
| ?- compile('pha-int.tex').

To load a rulebase "adderinf" do
| ?- thconsult(adderinf).


The code is in the file 'pha-int.tex'. This can be formatted using Latex
by changing one character at the beginning of the file.

The file 'pha-bn.ps' (in ftp/local/poole/papers) is a paper that
describes the theory behind probabilistic Horn abduction. It is to
appear in Artificial Intelligence.

The following are rule bases:
'adderinf' is a cascaded adder (as described in 'pha-bn.ps').
'bnet' is the Bayesian network described in 'pha-bn.ps'.
'depiction' is a depiction example (as in 'pha-bn.ps').
'inv3' is three cascaded inverters.
  


The following is a trace of a program (with my comments in upper case):

>prolog
Quintus Prolog Release 3.1 (Sun-4, SunOS 4.1)
Copyright (C) 1990, Quintus Corporation.  All rights reserved.
2100 Geng Road, Palo Alto, California U.S.A. (415) 813-3800

| ?- compile('pha-int.tex').
% compiling file /nfs/lci/ai1/poole/res/abduction/int/pha-int.tex
! Permission error: cannot redefine built-in predicate append/3
! goal:  assertz(append([],_8025,_8025))
IGNORE THIS - APPEND IS DEFINED FOR THOSE SYSTEMS THAT DON'T PREDEFINE IT
% pha-int.tex compiled in module user, 1.717 sec 10,740 bytes

yes
| ?- thconsult(adderinf).

yes
| ?- explain(( val(output(1,adder(1)),off,t2),
               val(output(1,adder(s(1))),off,t2),
               val(output(1,adder(s(s(1)))),off,t2),
               val(output(2,adder(s(s(1)))),on,t2) )).
Probability mass = [4.9403e-04,0.00397656]
THIS IS THE ESTIMATE OF THE PRIOR PROBABILITY OF THE OBSERVATION
Explanation: [ok(xor2(1)),ok(xor1(1)),ok(xor2(s(1))),ok(xor1(s(1))),ok(or1(1)),o
k(and2(1)),ok(and1(1)),ok(xor2(s(s(1)))),ok(xor1(s(s(1)))),stuck0(or1(s(1))),ok(
or1(s(s(1)))),ok(and2(s(s(1)))),ok(and1(s(s(1))))]
Prior = 4.9403e-04
THIS IS THE PRIOR PROBABILITY OF THE EXPLANATION
Posterior = [0.124236,1.0];
THIS IS THE CURRENT ESTIMATE OF THE POSTERIOR PROBABILITY OF THE EXPLANATION
Runtime: 20317 msec.

yes
| ?- more.
Probability mass = [9.8797e-04,0.00348238]
Explanation: [ok(xor2(1)),ok(xor1(1)),ok(xor2(s(1))),ok(xor1(s(1))),ok(or1(1)),o
k(and2(1)),ok(and1(1)),ok(xor2(s(s(1)))),stuck1(xor1(s(s(1)))),ok(or1(s(1))),ok(
and2(s(1))),ok(or1(s(s(1)))),ok(and2(s(s(1))))]
Prior = 4.9393e-04
Posterior = [0.141838,0.49995]
Runtime: 833 msec.

yes
| ?- more.
Probability mass = [0.00148151,0.0029882]
Explanation: [ok(xor2(1)),ok(xor1(1)),ok(xor2(s(1))),ok(xor1(s(1))),ok(or1(1)),o
k(and2(1)),ok(and1(1)),stuck0(xor2(s(s(1)))),ok(or1(s(s(1)))),ok(and2(s(s(1)))),
ok(or1(s(1))),ok(and2(s(1))),ok(xor1(s(s(1)))),ok(and1(s(s(1))))]
Prior = 4.9354e-04
Posterior = [0.165163,0.333133]
Runtime: 584 msec.

yes
| ?- more.
Probability mass = [0.00197455,0.00200112]
Explanation: [ok(xor2(1)),ok(xor1(1)),ok(xor2(s(1))),ok(xor1(s(1))),ok(or1(1)),o
k(and2(1)),ok(and1(1)),ok(xor2(s(s(1)))),ok(xor1(s(s(1)))),ok(or1(s(1))),stuck0(
and2(s(1))),ok(and1(s(1))),ok(or1(s(s(1)))),ok(and2(s(s(1)))),ok(and1(s(s(1))))]
Prior = 4.9305e-04
Posterior = [0.246384,0.2497]
Runtime: 383 msec.

yes
| ?- reestimate.
THIS ASKS FOR A REESTIMATE OF THE PROBABILITIES
Queue mass = 2.6573e-05
THIS IS AN UPPER BOUND ON THE PRIOR PROBABILITIES OF ALL OF THE EXPLANATIONS
NOT YET GENERATED
Probability mass = [0.00197455,0.00200112]
THIS IS AN ESTIMATE OF THE POSTERIOR PROBAILITY OF THE EXPLANATIONS
NOT YET GENERATED
Maximum prob not found = 0.0132789
THIS IS A BOUND ON THE POSTERIOR PROBABILITY OF THE EXPLANATIONS NOT YET
GENERATED (IS THE RELATIVE ERROR OF THE POSTERIOR PROBABILITIES).

Explanation: [ok(xor2(1)),ok(xor1(1)),ok(xor2(s(1))),ok(xor1(s(1))),ok(or1(1)),o
k(and2(1)),ok(and1(1)),ok(xor2(s(s(1)))),ok(xor1(s(s(1)))),stuck0(or1(s(1))),ok(
or1(s(s(1)))),ok(and2(s(s(1)))),ok(and1(s(s(1))))]
Prior = 4.9403e-04
Posterior = [0.246878,0.2502]
THIS IS A NEW ESTIMATE OF THE POSTERIOR PROBABILITY OF THE EXPLANATION

Explanation: [ok(xor2(1)),ok(xor1(1)),ok(xor2(s(1))),ok(xor1(s(1))),ok(or1(1)),o
k(and2(1)),ok(and1(1)),ok(xor2(s(s(1)))),stuck1(xor1(s(s(1)))),ok(or1(s(1))),ok(
and2(s(1))),ok(or1(s(s(1)))),ok(and2(s(s(1))))]
Prior = 4.9393e-04
Posterior = [0.246828,0.25015]

Explanation: [ok(xor2(1)),ok(xor1(1)),ok(xor2(s(1))),ok(xor1(s(1))),ok(or1(1)),o
k(and2(1)),ok(and1(1)),stuck0(xor2(s(s(1)))),ok(or1(s(s(1)))),ok(and2(s(s(1)))),
ok(or1(s(1))),ok(and2(s(1))),ok(xor1(s(s(1)))),ok(and1(s(s(1))))]
Prior = 4.9354e-04
Posterior = [0.246631,0.24995]

Explanation: [ok(xor2(1)),ok(xor1(1)),ok(xor2(s(1))),ok(xor1(s(1))),ok(or1(1)),o
k(and2(1)),ok(and1(1)),ok(xor2(s(s(1)))),ok(xor1(s(s(1)))),ok(or1(s(1))),stuck0(
and2(s(1))),ok(and1(s(1))),ok(or1(s(s(1)))),ok(and2(s(s(1)))),ok(and1(s(s(1))))]
Prior = 4.9305e-04
Posterior = [0.246384,0.2497]

yes

-----
If there are any problems please contact David Poole <poole@cs.ubc.ca>
