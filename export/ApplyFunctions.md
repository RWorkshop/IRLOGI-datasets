Using the “Apply” family of functions	
=========================================
Complex Simulation Program	
Cumulative Frequency Chart	
The Birthday function	
<hr>

Using the “Apply” family of functions

The "apply" family of functions keep you from having to write loops to perform some operation on every row or every column of a matrix or data frame, or on every element in a list.

#### The “apply()” function
The apply() function is a powerful device that operates on arrays and, in particular, matrices.
The apply() function returns a vector (or array or list of values) obtained by applying a specified function to either the row or columns of an array or matrix.
To specify use for rows or columns, use the additional argument of 1 for rows, and 2 for columns.

# create a matrix of 10 rows x 2 columns
m <- matrix(c(1:10, 11:20), nrow = 10, ncol = 2)

# mean of the rows

apply(m, 1, mean)
# [1]  6  7  8  9 10 11 12 13 14 15

# mean of the columns
apply(m, 2, mean)
#[1]  5.5 15.5

The local version of apply()is lapply(), which computes a function for each argument of a list., provided each argument is compatible with the function argument (e.g. that is numeric). 

The lapply() command returns a list of the same length as a list “X”, each element of which is the result of applying a specified function to the corresponding element of X.

A user friendly version of lapply() is sapply().

The sapply() command  is a variant of lapply() – returning a matrix instead of a list - again of the same length as a list X, each element of which is the result of applying a specified function to the corresponding element of X.

> x <- list(a=1:10, b=exp(-3:3), logic=c(T,F,F,T))
>
> # compute the list mean for each list element
>
> lapply(x,mean)
$a
[1] 5.5

$b
[1] 4.535125

$logic
[1] 0.5
>
> sapply(x,mean)
       a        b    logic 
5.500000 4.535125 0.500000
>
Complex Simulation Program

1)	Create a function called SumDice().
2)	Apply SumDice() n times to an initial value x
3)	Graph the data

SumDice = function(x){
	Temp1=sum(sample(1:6,x,replace=TRUE))
	return(Temp1)
	}

X=sapply(rep(100,100),SumDice)

DF1=data.frame(Index=1:1000,Sum=X)


Histogram and Cumulative Frequency Chart
Range of values quite interesting!!
Palette = c("blue","yellow","red","green")
hist(X,breaks=60:80*5,col=Palette)

#### The Birthday function
The R command pbirthday() computes the probability of a coincidence of a number of randomly chosen people sharing a birthday, given that there are n people to choose from.
Suppose there are four people in a room. The probability of two of them sharing a birthday can be computed as follows:
> pbirthday(4)
[1] 0.01635591

Answer:  about 1.6 %
How many people do you need for a greater than 50% chance of a shared birthday?
(starting from 2 – so the 5th element corresponds to 6 people, etc)

<pre><code>
 > sapply(2:60,pbirthday)
 [1] 0.002739726 0.008204166 0.016355912 0.027135574
 [5] 0.040462484 0.056235703 0.074335292 0.094623834
 [9] 0.116948178 0.141141378 0.167024789 0.194410275
[13] 0.223102512 0.252901320 0.283604005 0.315007665
[17] 0.346911418 0.379118526 0.411438384 0.443688335
[21] 0.475695308 0.507297234 0.538344258 0.568699704
[25] 0.598240820 0.626859282 0.654461472 0.680968537
[29] 0.706316243 0.730454634 0.753347528 0.774971854
[33] 0.795316865 0.814383239 0.832182106 0.848734008
[37] 0.864067821 0.878219664 0.891231810 0.903151611
[41] 0.914030472 0.923922856 0.932885369 0.940975899
[45] 0.948252843 0.954774403 0.960597973 0.965779609
[49] 0.970373580 0.974431993 0.978004509 0.981138113
[53] 0.983876963 0.986262289 0.988332355 0.990122459
[57] 0.991664979 0.992989448 0.994122661
</code></pre>
The answer is 23 people - probably much less than you thought!!



 

