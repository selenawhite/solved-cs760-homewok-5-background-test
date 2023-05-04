Download Link: https://assignmentchef.com/product/solved-cs760-homewok-5-background-test
<br>
The Wisconsin State Climatology Office keeps a record on the number of days Lake Mendota was covered by ice at <a href="http://www.aos.wisc.edu/~sco/lakes/Mendota-ice.html">http://www.aos.wisc.edu/</a><sup><a href="http://www.aos.wisc.edu/~sco/lakes/Mendota-ice.html">∼</a></sup><a href="http://www.aos.wisc.edu/~sco/lakes/Mendota-ice.html">sco/lakes/Mendota-ice.html.</a> Same for Lake Monona: <a href="http://www.aos.wisc.edu/~sco/lakes/Monona-ice.html">http://www.aos.wisc.edu/ </a><sup><a href="http://www.aos.wisc.edu/~sco/lakes/Monona-ice.html">∼</a></sup><a href="http://www.aos.wisc.edu/~sco/lakes/Monona-ice.html">sco/lakes/Monona-ice.html.</a> As with any real problems, the data is not as clean or as organized as one would like for machine learning. Curate two clean data sets for each lake, respectively, starting from 1855-56 and ending in 2018-19. Let <em>x </em>be the year: for 1855-56, <em>x </em>= 1855; for 2017-18, <em>x </em>= 2017; and so on. Let <em>y </em>be the ice days in that year: for Mendota and 1855-56, <em>y </em>= 118; for 2017-18, <em>y </em>= 94; and so on. Some years have multiple freeze thaw cycles such as 2001-02, that one should be <em>x </em>= 2001<em>,y </em>= 21.

<ol>

 <li>Plot year vs. ice days for the two lakes as two curves in the same plot. Produce another plot for year vs. <em>y</em><em>Monona </em>− <em>y</em><em>Mendota</em>.</li>

 <li>Split the datasets: <em>x </em>≤ 1970 as training, and <em>x &gt; </em>1970 as test. (Comment: due to the temporal nature this is NOT an iid split. But we will work with it.) On the training set, compute the sample mean and the sample standard deviation for the two lakes, respectively.</li>

 <li>Using training sets, train a linear regression model</li>

</ol>

<em>y</em>ˆ<em>Mendota </em>= <em>β</em>0 + <em>β</em>1<em>x </em>+ <em>β</em>2<em>y</em><em>Monona</em>

to predict <em>y<sub>Mendota</sub></em>. Note: we are treating <em>y<sub>Monona </sub></em>as an observed feature. Do this by finding the closedform MLE solution for <em>β </em>= (<em>β</em><sub>0</sub><em>,β</em><sub>1</sub><em>,β</em><sub>2</sub>)<sup>&gt; </sup>(no regularization):

<em>.</em>

Give the MLE formula in matrix form (define your matrices), then give the MLE value of <em>β</em><sub>0</sub><em>,β</em><sub>1</sub><em>,β</em><sub>2</sub>.

<ol start="4">

 <li>Using the MLE above, give the (1) mean squared error and (2) <em>R</em><sup>2 </sup>values on the Mendota test set. (You will need to use the Monona test data as observed features.)</li>

 <li>“Reset” to Q3, but this time use gradient descent to learn the <em>β</em>’s. Recall our objective function is the mean squared error on the training set:</li>

</ol>

<em>.</em>

Derive the gradient.

<ol start="6">

 <li>Implement gradient descent. Initialize <em>β</em><sub>0 </sub>= <em>β</em><sub>1 </sub>= <em>β</em><sub>2 </sub>= 0. Use a fixed stepsize parameter <em>η </em>= 0<em>.</em>1 and print the first 10 iteration’s objective function value. Tell us if further iterations make your gradient descent converge, and if yes when; compare the <em>β</em>’s to the closed-form solution. Try other <em>η </em>values and tell us what happens. Hint: Update <em>β</em><sub>0</sub><em>,β</em><sub>1</sub><em>,β</em><sub>2 </sub>simultaneously in an iteration. Don’t use a new <em>β</em><sub>0 </sub>to calculate <em>β</em><sub>1</sub>, and so on.</li>

</ol>

Homework 5                                                                                                                                    CS 760 Machine Learning

<ol start="7">

 <li>As preprocessing, normalize your year and Monona features (but not <em>y<sub>Mendota</sub></em>). Then repeat Q6.</li>

 <li>“Reset” to Q3 (no normalization, use closed-form solution), but train a linear regression model without using Monona:</li>

</ol>

<em>y</em>ˆ<em>Mendota </em>= <em>γ</em>0 + <em>γ</em>1<em>x.</em>

<ul>

 <li>Interpret the sign of <em>γ</em><sub>1</sub>.</li>

 <li>Some analysts claim that because <em>β</em><sub>1 </sub>the closed-form solution in Q3 is positive, fixing all other factors, as the years go by the number of Mendota ice days will increase, namely the model in Q3 indicates a cooling trend. Discuss this viewpoint, relate it to question 8(a).</li>

</ul>

<ol start="9">

 <li>Of course, Weka has linear regression. Reset to Q3. Save the training data in .arff format for Weka. Use classifiers / functions / LinearRegression. Choose “Use training set.” Bring up Linear Regression options, set “ridge” to 0 so it does not regularize. Run it and tell us the model: it is in the output in the form of “<em>β</em><sub>1 </sub>* year + <em>β</em><sub>2 </sub>* Monona + <em>β</em><sub>0</sub>.”</li>

 <li>Ridge regression.

  <ul>

   <li>Then set ridge to 1 and tell us the resulting Weka model.</li>

   <li>Meanwhile, derive the closed-form solution in matrix form for the ridge regression problem:</li>

  </ul></li>

</ol>

where

k<em>β</em>k<sup>2</sup><em><sub>A </sub></em>:= <em>β</em><sup>&gt;</sup><em>Aβ</em>

and

0    0    0

<em>A </em>= <sub></sub>0     1     0<sub></sub><em>.</em>

0    0    1

This <em>A </em>matrix has the effect of NOT regularizing the bias <em>β</em><sub>0</sub>, which is standard practice in ridge regression. Note: Derive the closed-form solution, do not blindly copy lecture notes.

<ul>

 <li>Let <em>λ </em>= 1 and tell us the value of <em>β </em>from your ridge regression model.</li>

</ul>

<h1>Extra Credit: Multinomial Na¨ıve Bayes</h1>

Consider the Multinomial Na¨ıve Bayes model. For each point (<strong>x</strong><em>,y</em>), <em>y </em>∈ {0<em>,</em>1}, <strong>x </strong>= (<em>x</em><sub>1</sub><em>,x</em><sub>2</sub><em>,…,x<sub>M</sub></em>) where each <em>x<sub>j </sub></em>is an integer from {1<em>,</em>2<em>,…,K</em>} for 1 ≤ <em>j </em>≤ <em>M</em>. Here <em>K </em>and <em>M </em>are two fixed integer. Suppose we have <em>N </em>data points {(<strong>x</strong><sup>(<em>i</em>)</sup><em>,y</em><sup>(<em>i</em>)</sup>) : 1 ≤ <em>i </em>≤ <em>N</em>}, generated as follows.

for <em>i </em>∈ {1<em>,…,N</em>}: <em>y</em><sup>(<em>i</em>) </sup>∼ Bernoulli(<em>φ</em>) for <em>j </em>∈ {1<em>,…,M</em>}:

Multinomial(<em>θ<sub>y</sub></em>(<em><sub>i</sub></em><sub>)</sub><em>,</em>1)

Here <em>φ </em>∈ R and <em>θ<sub>k </sub></em>∈ R<em><sup>K</sup></em>(<em>k </em>∈ {0<em>,</em>1} are parameters. Note that <sup>P</sup><em><sub>l </sub></em><em>θ<sub>k,l </sub></em>= 1 since they are the parameters of a multinomial distribution.

Derive the formula for estimating the parameters <em>φ </em>and <em>θ<sub>k</sub></em>, as we have done in the lecture for the Bernoulli Na¨ıve Bayes model. Show the steps.

<h1>Extra Credit: Logistic Regression</h1>

<ul>

 <li>Suppose for each class <em>i </em>∈ {1<em>,…,K</em>}, the class-conditional density <em>p</em>(<strong>x</strong>|<em>y </em>= <em>i</em>) is normal with mean <em>µ<sub>i </sub></em>∈ R<em><sup>d </sup></em>and the same covariance <strong>Σ </strong>∈ R<em><sup>d</sup></em><sup>×<em>d</em></sup>:</li>

</ul>

<em>p</em>(<strong>x</strong>|<em>y </em>= <em>i</em>) = <em>N</em>(<strong>x</strong>|<em>µ<sub>i</sub>,</em><strong>Σ</strong>)<em>.</em>

Compute <em>p</em>(<em>y </em>= <em>i</em>|<strong>x</strong>). Can it be represented as a softmax over a linear transformation of <strong>x</strong>? Show the calculation steps.

Homework 5                                                                                                                                    CS 760 Machine Learning

<ul>

 <li>Suppose <em>p</em>(<strong>x</strong>|<em>y </em>= <em>i</em>) has different covariances <strong>Σ</strong><em><sub>i </sub></em>∈ R<em><sup>d</sup></em><sup>×<em>d</em></sup>:</li>

</ul>

<em>p</em>(<strong>x</strong>|<em>y </em>= <em>i</em>) = <em>N</em>(<strong>x</strong>|<em>µ<sub>i</sub>,</em><strong>Σ</strong><em><sub>i</sub></em>)<em>.</em>

Again, compute <em>p</em>(<em>y </em>= <em>i</em>|<strong>x</strong>). Can it be represented as a softmax over a linear transformation of <strong>x</strong>? Show the calculation steps.