# Survey of Visual Feature Extraction Algorithms in a Mars-like environment

Martin Oelsch, Dominik Van Opdenbosch, Eckehard Steinbach, **Survey of Visual Feature Extraction Algorithms in a Mars-like Environment**. *IEEE International Symposium on Multimedia,Taichung, Taiwan* (2017).

## Description
Feature detection and description algorithms are widely used for computer vision applications, such as SLAM, object detection, content-based image retrieval, etc.
However, these algorithms were developed with focus on the Earth environment. This study presents a baseline research for a performance comparison of visual feature extraction algorithms in poorly-structured environments, e.g. as found on the planet Mars. These features can further be used in an unknown environment for autonomous Mars rovers to perform SLAM tasks.

For our performance comparison we used the Devon Island dataset [1]. In the following we provide a table with the combinations of feature detection and description algorithms used in our experiments, including their parametrization and implementations.

## Configuration
| Detector  |    Det. config.       | Descriptor | Descr. config.  | Descr. type | Descr. dim. | Implementation|
| --------- | --------------------- | ---------- | --------------- | ----------- | ----------- | ------------- |
|   SURF [2]   | threshold = 1e-08<br>octaves = 5 <br> intervals = 4 <br> init_sample = 2 |    SURF    | upright = false <br> use_kp_orient = false |    float    |      64     |    OpenSURF [3]   |
| SURF | as above | DAISY [4] | radius = 15 <br> q_radius = 3 <br> q_theta = 8 <br> q_hist = 8 <br> norm = none <br> interpolation = true <br> use_orientation = false | float | 200 | OpenSURF & OpenCV |
| SIFT [5] | - | SIFT | - | float | 128 | author's binary |
| LIFT [6] | - | LIFT | - | float | 128 | author's source code |
| MSER [7] | delta = 1 <br> min_area = 60 <br> max_area = 14400 <br> max_variation = 0.25 <br> min_diversity = 0.2 <br> norm_patch_size = 41 | SURF | as SURF above | float | 64 | OpenCV & OpenSURF |
| MSER | as above | DAISY | as DAISY above | float | 200 | OpenCV |
| MSER | as above | LIOP [8] | neighbors = 4 <br> spatial_bins = 6 <br> radius = 6 <br> side_length = 41 <br> threshold = -5/255 | float | 144 | OpenCV & VLFEAT |
| LBGM [9] | - | LBGM | - | float | 64 | author's source code |
| BRISK [10] | threshold = 30 <br> octaves = 4 <br> pattern_scale = 1 | BRISK | - | binary | 512 bit | OpenCV |
| BRISK | as above | FREAK [11] | orient_normalized = true <br> scale_normalized = true <br> pattern_scale = 22 <br> octaves = 4 | binary | 512 bit | OpenCV |
| ORB [12] | features = 1100 <br> scale_factor = 1.2 <br> levels = 8 <br> edge_threshold = 31 <br> first_level = 0 <br> score_type = Harris <br> fast_threshold = 30 | ORB | WTA_K = 2 <br> patch_size = 31 | binary | 256 bit | OpenCV |
| BINBOOST_64 [13] | - | BINBOOST_64 | - | binary | 64 bit | author's source code |
| BINBOOST_256 [13] | - | BINBOOST_256 | - | binary | 256 bit | author's source code |


## References
- [1] [Devon Island Rover Navigation Dataset](http://asrl.utias.utoronto.ca/datasets/devon-island-rover-navigation/rover-traverse.html#Overview)
- [2] H. Bay, A. Ess, T. Tuytelaars, and L. Van Gool, “Speeded-up robust features (surf),” Comput. Vis. Image Underst., vol.
110, no. 3, pp. 346–359, Jun. 2008.
- [3] [“Notes on the opensurf library”](http://www.cs.bris.ac.uk/publications/Papers/2000970.pdf)
- [4] E. Tola, V. Lepetit, and P. Fua, “A fast local descriptor for dense matching,” in Computer Vision and Pattern Recognition, 2008. CVPR 2008. IEEE Conference on. IEEE, 2008, pp. 1–8.
- [5] D. G. Lowe, “Distinctive image features from scale-invariant keypoints,”Int. J. Comput. Vision, vol. 60, no. 2, pp. 91–110, Nov. 2004.
- [6] K. M. Yi, E. Trulls, V. Lepetit, and P. Fua, “LIFT: learned invariant feature transform,” CoRR, vol. abs/1603.09114, 2016.
- [7] J. Matas, O. Chum, M. Urban, and T. Pajdla, “Robust wide-baseline stereo from maximally stable extremal regions,” Image and vision computing, vol. 22, no. 10, pp. 761–767, 2004.
- [8] Z. Wang, B. Fan, and F. Wu, “Local intensity order pattern for feature description,” in Proceedings of the 2011 International Conference on Computer Vision, ser. ICCV ’11. Washington, DC, USA: IEEE Computer Society, 2011, pp. 603–610.
- [9] T. Trzcinski, M. Christoudias, V. Lepetit, and P. Fua, “Learning image descriptors with the boosting-trick,” in Advances in Neural Information Processing Systems 25, F. Pereira, C. J. C. Burges, L. Bottou, and K. Q. Weinberger, Eds. Curran Associates, Inc., 2012, pp. 269–277.
- [10] S. Leutenegger, M. Chli, and R. Y. Siegwart, “Brisk: Binary robust invariant scalable keypoints,” in Proceedings of the 2011 International Conference on Computer Vision, ser. ICCV ’11. Washington, DC, USA: IEEE Computer Society, 2011, pp. 2548–2555.
- [11] R. Ortiz, “Freak: Fast retina keypoint,” in Proceedings of the 2012 IEEE Conference on Computer Vision and Pattern Recognition (CVPR), CVPR ’12. Washington, DC, USA: IEEE Computer Society, 2012, pp. 510–517.
- [12] E. Rublee, V. Rabaud, K. Konolige, and G. Bradski, “Orb: An efficient alternative to sift or surf,” in Proceedings of the 2011 International Conference on Computer Vision, ser. ICCV ’11. Washington, DC, USA: IEEE Computer Society, 2011, pp. 2564–2571.
- [13] T. Trzcinski, M. Christoudias, P. Fua, and V. Lepetit, “Boosting binary keypoint descriptors,” in 2013 IEEE Conference on Computer Vision and Pattern Recognition, June 2013, pp. 2874–2881.
