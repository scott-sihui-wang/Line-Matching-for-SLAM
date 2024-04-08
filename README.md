# Line Matching for SLAM

**Topics:** _Simultaneous Localization and Mapping (SLAM)_, _Stereo matching_, _Homography Estimation_, _Canny Line Detectors_

**Skills:** _OpenCV_, _C++_

This project corresponds to the paper `Multiple Homography Estimation via Stereo Line Matching for Textureless Indoor Scenes` that I published on `International Conference on Control, Automation and Robotics` (ICCAR 2019). This paper can be found online at [here](https://ieeexplore.ieee.org/document/8813439).

## Background and Motivation

In vision-based `SLAM` community, `point-based methods`, such as `SIFT`, are well-studied and widely used. However, `point-based methods` can't produce satisfactory results in _indoor_ environment where textured objects become less frequent.

As an alternative to `point-based methods`, `line-based methods` demostrate following advantages:

- `line-based methods` can utilize line features, which are abundant in man-made, indoor environment;

- `line-based methods` are less likely to make mistakes in the process of feature matching, and therefore can produce more _robust_ results;

- `line-based methods` can provide _structural information_ about the indoor environment.




## Paper Contribution

The major contributions of this paper are:

- Developed a unified approach for `line detection` and `stereo matching` that can produce appealing results in indoor textureless scenes.

- Proposed a co-planar line classification algorithm.

- Pointed out that the compatibility of multiple `homographies` can be improved by enforcing the `epipolar` line constraints.

## Our Hybrid Approach


The code here is our hybrid algorithm for line detection and stereo matching.

In https://github.com/slslam/slslam, J. Lee, S. Lee, G. Zhang, J. Lim and I. Suh proposed a Canny-based line extractor and integrated it with the MSLD descriptor for line detection and matching. It is shown that this line detection algorithm is capable of detecting weak textures as well as generating non-fragmented line segments.

In https://github.com/mtamburrano/LBD_Descriptor, L. Zhang and R. Koch proposed the LBD descriptor for line matching. According to them, LBD descriptor is more efficient to compute and it is faster to generate the matching results than the state-of-the-art methods.

However, there are a couple of drawbacks of the originally proposed LBD-based approach. First, in the originally proposed LBD-based approach, LBD descriptor is incorporated with EDLine detector and the latter is proved to be inefficient to detect low-contrast edges in our experiments. Second, in the originally proposed LBD-based approach, efforts are made to overcome the scale changes and the global rotation, which won't produce any improvement in our cases given that we apply the algorithm to calibrated, stereo cameras.

Our code has the advantages of both the Canny+MSLD approach and the EDLine+LBD approach and it can produce superior results in the indoor textureless scenes.

