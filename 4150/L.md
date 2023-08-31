* Time = # stpes used by  a TM
* space = num tape cells read/written by TM
* f(n) space Tm is one that sends from at most F(n) tape cells, for any input length n
* f(n) space NTM sends at most F(n) tape cells on each branch
	* Space(f(n)). =
 
#### SAT $\in$ space(?)
```
 brute force SAT($\phi$) 
	 for each assignment of T/F to variables of phi:
	 if phi is satisfied
		 accept
	 
```
n variables time ~ O(2^n) try 2^n configurations one assignment takes ~n space if assignment fails erase, overwrite new on eover top O(n) space
#####
SAT $\in$ space(n)
NP $\notin$ space(n)

#### Minor 
Difference Time/space
* space is resuable
idea to show that NP $\subseteq$ space(n)
* L $\in$ NP -> convert L to sat -> solve SAT in liner space -> solve L in linear space
	* we know we can do this because NP complete
		* only gaurantee that we get for space is that it is polynomial
	* goes from n^100 of time -> n^100 unary -> x
		* the space is not necessarily the same as the time
Note: Np != SPACE(n)
* Maybe NP $\subseteq$ space(n) or space(n) $\subseteq$ NP, but unknown

| n^2 time               | n^2 space       |
| ---------------------- | --------------- |
| unlimited space        | unlimited time  |
| this is strictly worse | Strictly better |
unlimited space can't be accessed in n^2 time
Thm: TIME(f(n)) $\subseteq$ SPACE(f(n)):
	proof in f(n) time can look at most f(n) cells
	note: TIME(f(n)) $\subset$ Space(f(n))
	PSPACe = $\cup_i$ SPACE(ni) 
	NPSPACE = $\cup_i$ NSPACE(u^i)

 WE know P $\subseteq$ PSPACE
	pf: L $\in$ P, $L\in$ TiME(ni) -> L $\in$ Space(ni) -> L $\in$ PSPACE 
		NP $\subseteq$ PSPACE
	L $\in$ NP -> L to sat -> sat \in pspace -> 2 \in pspace
							in poly time
	know: P $\subseteq$ NP $\subseteq$ PSPACE 
		p = pspace -> p = np

Use F(n) memory -> run for how many steps
* F(n) | must always be halt |
configureation: tape contents, taphead location, state
* if you ever repeat configurations, you are stuck in a loop
* if M uses f(n) memory, doesn't loop -> # steps <= # configurations
| State | tapehead location | tape contnets                         |     |
| ----- | ----------------- | ------------------------------------- | --- |
| size(Q)     | f(n)                 | f(n cells), sigma symbols, sigma^f(n) |     |
num configs: |Q| * f(n) * sigma^f(n) -> 2^O(f(n))

PSPACE $\subseteq$ EXPTIME
EXPTIME = $\cup_i$ TIME($2^{n^i}$)
	P $\subseteq$ NP $\subseteq$  Pspace $\subseteq$  exptime
	think: p $\subset$  NP $\subset$ pspace $\subset$ exptime
	know: p $\subseteq$  exptime

thm: psapce = npspace
savitch?: Nspace(f(n)) $\subseteq$ space(f(n)^2)
	Assume: L is in nspace(f(n)) -> some f(n) space ntm decides L
	-> create N'  -> deterministic TM for L -> (L $\in$ space(f(n)^2)

	convert NTMP to DTM 3 steps
	1. inpute (newer changes)
	2. simulate N on input
	3. current sequence of choices

	space: 
	1. n space
	2. f(n) space
	3. one choice per step

