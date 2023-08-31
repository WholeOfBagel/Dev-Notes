Sampling
* sample the 2d space on grid -> quantize each sample (int)
	* one value per pixel
* sample across R, G, B (can be avged together for one image)

Filter (denoise, resize, extract texture, edges, detect patterns)
* enhance image - denoise
	* raw pixel of same image won't be same
* Salt and pepper: white pixels - guassian noise sample from guassian N(u, sigma) more var = more noise

Reducing noise: average of neighbors - expect neighbors to be similar [1, 1, 1, 1, 1]/5 (uniform)
[1, 4, 5, 4, 1]/16
==Correlation filtering: G[i,j] = 1/(2k+1)^2 $\sum_{u=-k}^{k}(\sum_{v =-k}^{k}{F[i + u +, j + v]})$ G = HxF== H is mask produces flipped -> convolution then apply cross (symmetric will output same)
* H = 1/9 [matrix of 1's] 
* ![[Pasted image 20230305202304.png]]
* full = any part of g touches f, same = same size as f, valid = doesn't fall of edge
* boundary (clip filter black, wrap around, copy edge, reflect across edge)
* window size doesn't imapct gaussian -but variance does directly (filter size ~ 6$\sigma$) choose window size from this
* remove hf; low pass filter
Runtime: O(n^2m^2) -> 1d G * 1d G = 2d G O(N) (by seperability outer product)

prop: convolution is linear, can shift
Non-linear filters: median (comp heavy)
low freq: smoothing
high freq: og + (og - smooth = details)



![[Pasted image 20230305203431.png]]