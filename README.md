# How-to-kfold-Cross-Validation

october 22, 2018

I appreciate comments. Shoot me an email at noel_s_cruz@yahoo.com!

Hire me!

To make the cross-validation procedure concrete, let’s look at a worked example.

Imagine we have a data sample with 6 observations:

data = array([0.1, 0.2, 0.3, 0.4, 0.5, 0.6])

The first step is to pick a value for k in order to determine the number of 
folds used to split the data. Here, we will use a value of k=3. That means we
will shuffle the data and then split the data into 3 groups. Because we have 6
observations, each group will have an equal number of 2 observations.

For example:

Fold1: [0.5, 0.2]

Fold2: [0.1, 0.3]

Fold3: [0.4, 0.6]

We can then make use of the sample, such as to evaluate the skill of a machine
learning algorithm.

Three models are trained and evaluated with each fold given a chance to be the
held out test set.

For example:

Model1: Trained on Fold1 + Fold2, Tested on Fold3

Model2: Trained on Fold2 + Fold3, Tested on Fold1

Model3: Trained on Fold1 + Fold3, Tested on Fold2

The models are then discarded after they are evaluated as they have served 
their purpose.

The skill scores are collected for each model and summarized for use.

##############
Cross-Validation API
We do not have to implement k-fold cross-validation manually. The scikit-learn
library provides an implementation that will split a given data sample up.

The KFold() scikit-learn class can be used. It takes as arguments the number of
splits, whether or not to shuffle the sample, and the seed for the pseudorandom
number generator used prior to the shuffle.

For example, we can create an instance that splits a dataset into 3 folds, 
shuffles prior to the split, and uses a value of 1 for the pseudorandom number
generator.

# scikit-learn k-fold cross-validation

from numpy import array

from sklearn.model_selection import KFold

# data sample

data = array([0.1, 0.2, 0.3, 0.4, 0.5, 0.6])

# prepare cross validation

kfold = KFold(3, True, 1)

# enumerate splits

for train, test in kfold.split(data):

  print('train: %s, test: %s' % (data[train], data[test]))
  
Running the example prints the specific observations chosen for each train and
test set. The indices are used directly on the original data array to retrieve 
the observation values.

train: [ 0.1  0.4  0.5  0.6], test: [ 0.2  0.3]

train: [ 0.2  0.3  0.4  0.6], test: [ 0.1  0.5]

train: [ 0.1  0.2  0.3  0.5], test: [ 0.4  0.6]

Usefully, the k-fold cross validation implementation in scikit-learn is
provided as a component operation within broader methods, such as grid-searching
model hyperparameters and scoring a model on a dataset.

Nevertheless, the KFold class can be used directly in order to split up a 
dataset prior to modeling such that all models will use the same data splits. 
This is especially helpful if you are working with very large data samples. The
use of the same splits across algorithms can have benefits for statistical 
tests that you may wish to perform on the data later.

I included some posts for reference.

https://github.com/noey2020/How-to-Talk-Statistics-Pattern-Recognition-101

https://github.com/noey2020/How-to-Write-SPI-STM32

https://github.com/noey2020/How-to-Write-SysTick-Handler-for-STM32

https://github.com/noey2020/How-to-Write-Subroutines-in-C-Assembly-STM32

https://github.com/noey2020/How-to-Write-Multitasking-STM32

https://github.com/noey2020/How-to-Generate-Triangular-Wave-STM32-DAC

https://github.com/noey2020/How-to-Generate-Sine-Table-LUT

https://github.com/noey2020/How-to-Illustrate-Multiple-Exceptions-

https://github.com/noey2020/How-to-Blink-LED-using-Standard-Peripheral-Library

I appreciate comments. Shoot me an email at noel_s_cruz@yahoo.com!

Hire me!

Have fun and happy coding!
