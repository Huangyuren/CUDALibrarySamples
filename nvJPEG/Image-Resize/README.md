# Image Resize Example using nvJPEG

## Description

This code demonstrates Image resize utility using NPP resize and nvJPEG library.

## Key Concepts

Image Resize, Image Encoding and Decoding from NVJPEG Library

## Supported SM Architectures

[SM 3.0 ](https://developer.nvidia.com/cuda-gpus)  [SM 3.5 ](https://developer.nvidia.com/cuda-gpus)  [SM 3.7 ](https://developer.nvidia.com/cuda-gpus)  [SM 5.0 ](https://developer.nvidia.com/cuda-gpus)  [SM 5.2 ](https://developer.nvidia.com/cuda-gpus)  [SM 6.0 ](https://developer.nvidia.com/cuda-gpus)  [SM 6.1 ](https://developer.nvidia.com/cuda-gpus)  [SM 7.0 ](https://developer.nvidia.com/cuda-gpus)  [SM 7.2 ](https://developer.nvidia.com/cuda-gpus)  [SM 7.5 ](https://developer.nvidia.com/cuda-gpus)

## Supported OSes

Linux Windows

## Supported CPU Architecture

x86_64

## CUDA APIs involved
[NPP](https://docs.nvidia.com/cuda/npp/group__image__resize.html)
[NVJPEG](https://docs.nvidia.com/cuda/nvjpeg/index.html)


# Architecture
- JPEG decoding is handled by nvJPEG.
- Image resizing is handled by NPP (algorithm: Lanczos)
- JPEG encoding is handled by nvJPEG.

# Building (make)

# Prerequisites
- A Linux/Windows system with recent NVIDIA drivers.
- Install the [CUDA 10.1 toolkit](https://developer.nvidia.com/cuda-downloads).

## Build command on Linux
```
$ mkdir build
$ cd build
$ cmake ..
$ make
```

## Build command on Windows
```
$ mkdir build
$ cd build
$ cmake -DCMAKE_GENERATOR_PLATFORM=x64 ..
$ Open imageResize.sln project in Visual Studio 15 2017 and build
```




# Usage
./imageResize -h
```
Usage: ./imageResize -i images-dir  [-o output-dir][-q jpeg-quality][-rw resize-width ] [-rh resize-height]
Parameters: 
	images-dir	:	Path to single image or directory of images
	output-dir	:	Write resized images to this directory [default resize_output]
	JPEG Quality	:	Use image quality [default 85]
	Resize Width	:	Resize width [default original_img_width/2]
	Resize Height	:	Resize height [default original_img_height/2]

```
Example:
```
-i input_images - JPEG input images
-o resize_images - resize output images
-q 85 - setting encoder quality 85
-rw 512 - resize width set to 512
-rh 512 - resize height set to 512
```
```
$  ./imageResize -i ../input_images/ -o resize_images -q 85 -rw 512 -rh 512

```

Sample example output on GV100, Ubuntu 18.04, CUDA 10.1

```
$  ./imageResize -i ../input_images/
```
```
Processing file: ../input_images/cat_baseline.jpg
Resize-width: 32 Resize-height: 32
Writing JPEG file: resize_output/cat_baseline.jpg
Processing file: ../input_images/img8.jpg
Resize-width: 240 Resize-height: 320
Writing JPEG file: resize_output/img8.jpg
Processing file: ../input_images/img5.jpg
Resize-width: 320 Resize-height: 240
Writing JPEG file: resize_output/img5.jpg
Processing file: ../input_images/img7.jpg
Resize-width: 240 Resize-height: 320
Writing JPEG file: resize_output/img7.jpg
Processing file: ../input_images/img2.jpg
Resize-width: 240 Resize-height: 320
Writing JPEG file: resize_output/img2.jpg
Processing file: ../input_images/img4.jpg
Resize-width: 320 Resize-height: 213
Writing JPEG file: resize_output/img4.jpg
Processing file: ../input_images/cat.jpg
Resize-width: 32 Resize-height: 32
Writing JPEG file: resize_output/cat.jpg
Processing file: ../input_images/cat_grayscale.jpg
Resize-width: 32 Resize-height: 32
Writing JPEG file: resize_output/cat_grayscale.jpg
Processing file: ../input_images/img1.jpg
Resize-width: 240 Resize-height: 320
Writing JPEG file: resize_output/img1.jpg
Processing file: ../input_images/img3.jpg
Resize-width: 320 Resize-height: 213
Writing JPEG file: resize_output/img3.jpg
Processing file: ../input_images/img9.jpg
Resize-width: 320 Resize-height: 240
Writing JPEG file: resize_output/img9.jpg
Processing file: ../input_images/img6.jpg
Resize-width: 320 Resize-height: 240
Writing JPEG file: resize_output/img6.jpg
------------------------------------------------------------- 
Total images resized: 12
Total time spent on resizing: 35.9706 (ms)
Avg time/image: 2.99755 (ms)
-------------------------------------------------------------
```

