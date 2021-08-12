# yolov5s_android:rocket: 
<div align="center">
<img src="https://github.com/lp6m/yolov5s_android/raw/media/android_app.gif" width=50%>
</div>
The implementation of yolov5s on android for the [yolov5s export contest](https://github.com/ultralytics/yolov5/discussions/3213)  


## Overview

## Performance
### Latency (inference)
These results are measured by [TFLite Model Benchmark Tool with C++ Binary](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/lite/tools/benchmark#profiling-model-operators) and `Xiaomi Mi11`.  
The latency does not contain the pre/post processing time and data transfer time.  
#### float32 model  

|       delegate        | latency [ms] |
| :-------------------- | -----------: |
| None (CPU)            |          xxx |
| NNAPI (qti-gpu, fp32) |          xxx |
| NNAPI (qti-gpu, fp16) |          xxx |
  
#### int8 model
We tried to accelerate the inference process by using `NNAPI (qti-dsp)` and offload calculation to Hexagon DSP, but it didn't work for now. Please see issue.
<!-- set issue number -->

|       delegate       | latency [ms] |
| :------------------- | -----------: |
| None (CPU)           |          xxx |
| NNAPI  (qti-default) |          xxx |
| NNAPI  (qti-dsp)     |   Not worked |

### Latency (inference + postprocess)

## Accuracy
<!-- change link to master after merge -->
Please refer [host/README.md](https://github.com/lp6m/yolov5s_android/tree/dev/host#example2) about the evaluation method.    
We set `conf_thresh=0.25` and `iou_thresh=0.45` for nms parameter.
|     device /  delegate      | mAP  |
| :-------------------------- | ---: |
| host GPU (Tflite + PyTorch) | 27.8 |
| NNAPI  (qti-gpu, fp16)      | 28.5 |
| None   (int8)               |  xxx |


## Model conversion
This project focuses on obtaining a tflite model by model conversion from PyTorch original implementation, rather than doing its own implementation in tflite.  


## TODO
