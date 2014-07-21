Car Recognition
======

Description
-----
A tool which will analyse submitted images, and attempt to classify them through image recognition by manufacturer.
It will be built on top of the [OpenCV](http://opencv.org) library.


Classifiers:
----

   * classifier by manufacturer
      * does it need to be by model type?
         * is generic Porsche (for example) classifier sufficient?
         * or do need 996, 997, Cayman, Boxster etc
      * separate classifiers for angle types (front, side, rear etc)
   * HAAR or LBP?
      * LBP potentially much quicker to train?
      * Which has greater accuracy for given training time?
         * (LBP could be trained with more images in same time?)
   * Accuracy?
      * how many training images are sufficient to get >70% accuracy
      * curve of accuracy… graph on time to train vs accuracy over different sized sets of prospects.
   * online training of classifiers?




Application:
----

   * take input files (image), add to queue.
   * have classifier workers pull images off the queue, attempt each form of classifier in turn (most populate types first)
   * worker output is:
      * If single classifier matched, mark file with classifier (exif tag with keywords??) 
      * if multiple classifiers match, then review confidence for each classifier
         * if confidence is much higher for one match then mark as probably that
            * mark for verify, and re-train the one which false positived.
         * if confidence is similar, mark as false positive and mark for review
      * if no classifiers match, then mark as verify needed.


Background Reading:
----

   * [http://www.vision.ee.ethz.ch/~hegrabne/papers/Grabner2008TrainingSequentialOn-lineBoosting.pdf](http://www.vision.ee.ethz.ch/~hegrabne/papers/Grabner2008TrainingSequentialOn-lineBoosting.pdf)
   * [http://en.wikipedia.org/wiki/Online_machine_learning](http://en.wikipedia.org/wiki/Online_machine_learning)
   * [http://web.mit.edu/seyda/www/Papers/GHC06_ACMSRC_abstract.pdf](http://web.mit.edu/seyda/www/Papers/GHC06_ACMSRC_abstract.pdf)
   * [http://lmb.informatik.uni-freiburg.de/papers/download/fe_za_bu_GFKL07.pdf](http://lmb.informatik.uni-freiburg.de/papers/download/fe_za_bu_GFKL07.pdf)
   * [http://www.svms.org/training/ChLi.pdf](http://www.svms.org/training/ChLi.pdf)
   * [http://www.csie.ntu.edu.tw/~cjlin/papers/newsvr.pdf](http://www.csie.ntu.edu.tw/~cjlin/papers/newsvr.pdf)
   * [http://dsp.stackexchange.com/questions/3149/online-boosting-training-on-the-fly-for-face-detection](http://dsp.stackexchange.com/questions/3149/online-boosting-training-on-the-fly-for-face-detection)
   * [http://stackoverflow.com/questions/8791178/haar-cascades-vs-lbp-cascades-in-face-detection](http://stackoverflow.com/questions/8791178/haar-cascades-vs-lbp-cascades-in-face-detection)
   * [http://opencv-users.1802565.n2.nabble.com/LBP-vs-haar-cascades-td7312041.html](http://opencv-users.1802565.n2.nabble.com/LBP-vs-haar-cascades-td7312041.html)
   * [http://hal.inria.fr/docs/00/62/43/60/PDF/Finalversion_Haar_like_and_LBP_based_features.pdf](http://hal.inria.fr/docs/00/62/43/60/PDF/Finalversion_Haar_like_and_LBP_based_features.pdf)