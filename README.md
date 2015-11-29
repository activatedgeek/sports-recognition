# Sports Recognition in Videos

This repository builds a classifier to predict the sport being played. It works
on the UCF Sports dataset and builds a multi-class classifier based on SVM using
chi-squared kernel.

### Prerequisites
* [The UCF Sports Dataset](http://crcv.ucf.edu/data/UCF_Sports_Action.php), a
stripped down version (with no image dumps) can be found [here](https://www.dropbox.com/sh/e3r7jonuprxiqhn/AAD9wRI3lfqOrrYN8aY4yXMDa?dl=0)
* [Dense Trajectory Features](https://lear.inrialpes.fr/people/wang/dense_trajectories), this code has been included in `dense_trajectory_release_v1.2` folder

### Project Setup
Run `setup.sh` to install all dependencies. It also builds a `DenseTrack` executable
which gives out the features of all videos

### Code Flow
* The `DenseTrack` executable computes a large feature vector comprising of
HOG + HOF + MBH descriptors concatenated with each other
* The data is split into train and test with a ratio `test_size`
* A codebook of size `k` using k-means clustering is generated in `attempts`
* A bag-of-visual-words representation is created for each video using the
histogram built using the above clustering
* All the bag-of-visual-words are fed into the SVM using chi-squared kernel
and classified using a One-Vs-Rest Classifier

### Evaluation
The code has been evaluated on accuracy of predictions after the test and train
split ratio of 0.3.