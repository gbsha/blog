# Generalized Mutual Information

## Channel Coding Theorem by Maximum Likelihood Decoding

A discrete time channel with inputs $x_i$ and outputs $y_i$, $i=1,2,\dotsc, n$ is called memoryless, if
$$P_{Y^n|X^n}(y^n|x^n)=\prod_{i=1}^n P_{Y|X}(y_i|x_i)$$
that is, given the input $x^n$, the outputs are independent and distributed according to $P_{Y|X}(\cdot|x_i)$, $i=1,2,\dotsc, n$.

Consider a rate $R$ code 
$\mathcal{C}=\lbrace c^n(1),c^n(2),\dotsc, c^n(2^{nR})\rbrace$. A maximum-likelihood (ML) decoder uses the decoding rule 
$$\hat{w}=\underset{w\in\{1,\dotsc,2^{nR}\}}{\text{arg max}}\prod_{i=1}^n P_{Y|X}(y_i|c_i(w))$$

The channel coding theorem states that there exists a sequence of codes for which under ML decoding, the error probability $\Pr(W\neq\hat{W})$ approaches zero as the code length $n$ approaches infinity, if the rate is smaller than the mutual information of channel input and channel output, i.e., if
$$R<\mathbb{I}(X;Y).$$

This part of the channel coding theorem is called the "direct" or "achievability" part. There is also the converse part, which states that rates higher than capacity are not achievable; we will not talk about the converse part here.

A proof of the direct part using ML decoding can be found in [1, Chapter 5] and [2]. In [3], a typicality decoder is used instead of an ML decoder.

## A First Look at Generalized Mutual Information

For uniformly distributed input $X$, the ML rule can also be written as
$$\underset{w\in\{1,\dotsc,2^{nR}\}}{\text{arg max}}\prod_{i=1}^n P_{Y|X}(y_i|c_i(w)) = \underset{w\in\{1,\dotsc,2^{nR}\}}{\text{arg max}}\prod_{i=1}^n \frac{P_X(c_i(w))P_Y(y_i)}{P_Y(y_i)} P_{Y|X}(y_i|c_i(w))=\underset{w\in\{1,\dotsc,2^{nR}\}}{\text{arg max}}\prod_{i=1}^n P_{X|Y}(c_i(w)|y_i)$$
where $P_{X|Y}(x|y)$ is the a posteriori probability (APP) that the channel input was $x$, given that $y$ was observed at the channel output.

Writing out the mutual information, we have
$$\mathbb{I}(X;Y)=\mathbb{H}(X)-\mathbb{H}(X|Y)=\mathbb{H}(X)-\sum_y P_Y(y)\sum_{x}P_{X|Y}(x|y)[-\log_2 P_{X|Y}(x|y)].$$
We note that $P_{X|Y}$ appears in the decoding rule, and it also appears in the expansion of the mutual information. We may now assume some other APP distribution $Q_{X|Y}$ for decoding, different from the "true" APP distribution $P_{X|Y}$. How should be modify the mutual information to account for that $Q_{X|Y}$ was used for decoding and not $P_{X|Y}$? Note that $P_{X|Y}$ appears twice in the mutual information, namely as weighting factor in front of the logarithm, and as argument of the logarithm, which of the two occurences should we replace by $Q_{X|Y}$? Writing mutual information using the expectation operator provides the right intuition. We have
$$\mathbb{I}(X;Y)=\mathbb{H}(X)-\mathbb{H}(X|Y)=\mathbb{H}(X)-\mathbb{E}[-\log_2 P_{X|Y}(X|Y)]\geq \mathbb{H}(X)-\mathbb{E}[-\log_2 Q_{X|Y}(X|Y)]$$
where by the information inequality, we have equality if and only if $Q_{X|Y}=P_{X|Y}$.

* The right-hand side is a preliminary form of the generalized mutual information (GMI).
* The GMI provides an achievable rate for the case when a decoding rule different from the ML rule is used.
* Using a rule different from the ML rule possibly reduces the achievable rate.

## References

[1] R. G. Gallager, *Information theory and reliable communication*, 1968.

[2] G. Kramer, *Information Theory*, lecture notes, Technical University of Munich.

[3] T. M. Cover, A. T. Joy, *Elements of Information Theory*, 2006.