# Joint Probabilistic Data Association Tracking (JPDAFTracker)
JPDAFTracker is a tracker based on joint probabilistic data association filtering.

<p align="center">
<a href="https://www.youtube.com/watch?v=KlXpaKh8hDY"  target="_blank"><img src="https://img.youtube.com/vi/KlXpaKh8hDY/0.jpg"/></a>
</p>
<br>

## Requirements
* OpenCV
* Eigen

## How to build

JPDAFTracker works under Linux environments. I recommend a so-called out of source build which can be achieved by the following command sequence:

* mkdir build
* cd build
* cmake ../
* make -j<number-of-cores+1>

## Params
```bash
[PD] #DETECTION PROBABILITY
1

[PG] #GATE PROBABILITY
0.4

[LOCAL_GSIGMA] #THRESHOLD OF GATING
15

[LOCAL_ASSOCIATION_COST] #ASSOCIATION COSTS
40

[GLOBAL_GSIGMA] #THRESHOLD OF GATING
0.1

[GLOBAL_ASSOCIATION_COST] #ASSOCIATION COSTS
50

[LAMBDA] #CONSTANT
2

[GAMMA] #G1,G2 INITIAL COVARIANCE P MATRIX
10 10

[R_MATRIX] #2x2 MEASUREMENT NOISE COVARIANCE MATRIX
100 0
0 100

[DT] #dt
0.4

[MIN_ACCPETANCE_RATE] #min rate for convalidating a track
10

[MAX_MISSED_RATE] #max rate for deleting a track
9
```

## How to use

### Requires: 
- [x] Boxes are given in the detection.txt file, 1 row per one image, starting by the image index (must be 1) i.e.
```
1,5,386,193,41,15,517,239,84,37,623,36,45,28,484,187,56,21,516,251,38,19
``` 
where 1: index of the 1st frame. Corresponding image should be "%06d.jpg"%(img_frame); 5: number of objects ; 
following numbers represent bboxes (top left x, top left y, width, hight)


Go to the bin diretory and launch the program with the following command:
```bash
./jpdaf_tracker ../config/kalman_param.txt /path/to/the/detection_file.txt /path/to/the/image_folder 
```

## Example
![JPDAF Example](output_samples/jpdaf.gif)
