# Martingale Preserving Tree Algorithm

An important feature of the popular three factor trinomial tree is that it uses a deterministic approximation of the interest rates for constructing the stock tree. The preservation of the martingale property of the stock price is thus not guaranteed.  and may potentially represent a problem.

We propose a two-factor tree model that implements the Hull-White and Black-Karasinski models. The new tree model does preserve the martingale property of the stock for sufficiently long terms (with accuracy better that 10-8 for terms of at least 10 years). 

The three factor model assumes that under the risk neutral probability measure the stock price follows the stochastic process

 					(1)

and the interest rate process is governed by the Ho-Lee model:

 ,					(2)

where qS is the dividend rate. The Brownian motions W rt  and W St are supposed to be correlated. Next, the model makes an approximation and assumes that rt  in eq. (1) is a deterministic variable rS such that 

  					(3)

where P(0,t) is the price at time 0 of zero coupon bond maturing at t. As a result, the random walk parts of the S and r are only coupled through the linear stochastic terms in equations (1) and (2). This makes it possible to construct two individual one-factor tree, one for the S process and the other for the r process, which are then combined in a two-factor tree. 

The coupon is the nominal annual rate of interest that is paid to the holder on a regular basis. It is usually expressed as a percentage of the face value (coupon rate: https://finpricing.com/lib/FiBondCoupon.html). The coupon rate is either fixed or variable. The coupon rate is given as an annualized percentage of the face value.

The probabilities of the joint Brownian motion on the combined tree are adjusted according to the correlation between W rt and W St. This approach produces an efficient implementation, since it uses only two one-dimensional trees. It has a significant drawback, however: the martingale property of the stock price is not preserved. 

The new model assumes the rate process to be governed by the SDE

 ,				(4)

where x is r for the Hull-White model, or log(r) for the Black-Karasinski model.
The stock price is supposed to follow the stochastic process

 		(5)

where W rt  and W St are independent Brownian motions and  is the correlation coefficient.

Since eq. (4) is independent of eq. (5), the interest rate process is a one-factor process and the corresponding tree is constructed in the standard manner.

Eq. (5) depends on two factors, and the equity tree is built as a genuine two-dimensional tree.  Its r-projection replicates the above interest rate tree, with the same values of r and transition probabilities at the corresponding nodes in the r-dimension. The distribution of the stock values is calculated from eq. (5) and the overall transition probabilities are adjusted so as to preserve the martingale property and, if possible, to match the variance. The new trees allow variable time steps.


