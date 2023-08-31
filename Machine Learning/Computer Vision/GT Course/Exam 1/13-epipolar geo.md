Stereo: given 2 cameras/correspondence
* find: world coordinate for known point

### Epipolar Geometry
baseline connects both origins
* epioles where baseline intersects w img planes
* epiploar lines btw point and e -> p' (must be from same light ray)
	* rays given by ep line
* only translation -> ep lines horizontal, e $\infty$
* forward motion -> ep lines out from optical cent

### Calibrated case
* know intrinsic & extrinsic -> set coord to cam 1
	* $M_{1}= K[I, 0]$, $M_{2}= K'[R, t]$, M produce p
* $K^{-1}p$ producing normailized coordinate p^ with K as identity matrix (canonical view)
* coplanar: Rp^, t, p^ -> ![[Pasted image 20230308080800.png|100]]
*  ![[Pasted image 20230308080851.png|200]]
	* $x^{T}Ey = 0$ E is t_x: essential matrix
		* bc of p^ being normalized
		* ![[Pasted image 20230308081400.png|100]] E = $[t_x]R$ 
	* Ep^ gives eq for ep line for o'
	* E^Tp^ gives ep in o
	* epipoles in nullspace of E: ![[Pasted image 20230308081611.png|150]]
* ![[Pasted image 20230308081705.png|200]] Fp F^tp' are ep lines w p, p'
* Fe = 0 F^te' = 0, F r=2, F 7 deg freedom, !unique
* -> need at least 7 correspondences 
### eight point algo 
![[Pasted image 20230308082039.png|500]]
* f output is not perfect (bc not perfectly aligned)
* closest matrix F with lower rank = take highs $\sigma$
	* multiply SVD out for new F
1. normalize img coordinates: center img data @ origin 0> scale msd btw orgina & data points = 2
2. apply 8-point algo: compute  F
3. enforce rank-2 constraint
4. unnormalize coordinates: F back to og units
5. $T'^{T}FT =$ og coords
![[Pasted image 20230308082613.png|300]]

