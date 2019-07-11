# FETs - A Second Take on a Thesis Project

<p align="center">
  <img src="doc/img/shark.png" width="256" height="256" border="0" />
</p>

In 1988, I received my Ph.D. from Purdue University, and as part of that
thesis, this code was written to simulate, in two dimensions, and time, the
internal state of the device as it was under bias. The details of the code
are really best described in the Thesis, which is still available from
_University Microfilms_, which is interesting to me today... but hey, it's not
a lot of storage, so why not?

## Input File Format

_Shark_ is based on an _input deck_ like so many codebases that were meant
to run on supercomputers without even so much as terminal access. One such
input file is:
```
*
* This will be a comparative test of Sutherland's work for a Silicon
* MOSFET with SiO2, biased into weak inversion, triode mode
*
source thick=0.35
drain thick=0.35
bulk doping=2.0e16
oxide type=SiO2 thick=1000
channel type=MODFET length=3.0 material=Si
* setting dDo=0 will make D constant
DvsE Do=18.13 dDo=0.0
* setting A=C=inf. will make vsat=inf. and then v=u*E
VvsE mobility=700.0 A=2.0e38 C=2.0e38
* bias the device in the triode region
bias vsource=0.00 vdrain=0.35 eavg=0.0 vg1=2.5
* do the steady state operation: delt -> infinity
time tout=10.0 tstop=100.0 delt=1.0e38
solution type=linpk
start with=DC maxit=300 debug=sortof guess=MOS
```
and simulates a simple MISFET transistor in weak-inversion, triode operation.
This was a similar test case given in Sutherland's work, and was used to check
that _Shark_ was matching his work for correctness.

