# YOLOv5 Object Detection - COCO Dataset

This repository contains an implementation of object detection using the YOLOv5 (You Only Look Once version 5) model, which has been custom-trained on the COCO dataset using PyTorch. The model can detect objects in both images and video streams. It can also output the confidence score and bounding boxes for detected objects.

## Features

- **YOLOv5 Object Detection**: Trained model for detecting objects from the COCO dataset.
- **Image and Video Support**: Detect objects in both static images and video files.
- **Bounding Box & Confidence**: Provides bounding boxes and confidence scores for each detected object.

## Prerequisites

- Python 3.8 or higher
- PyTorch (compatible with your system's CUDA version for GPU support)
- Required Python libraries from the `requirements.txt`

## Installation

### Step 1: Clone the repository

```bash
git clone https://github.com/your-username/yolov5-object-detection.git
cd yolov5-object-detection
```

### Step 2: Install dependencies

Install the required Python packages using the following command:

```bash
pip install -r requirements.txt
```

You can manually install PyTorch if you don’t have it yet:

```bash
pip install torch torchvision torchaudio
```

### Step 3: Download COCO Dataset

Download the COCO dataset from the official [COCO website](https://cocodataset.org/#download). You'll need the `train2017`, `val2017`, and `annotations` folders for training the model.

## Training the Model

1. Prepare the dataset folder structure:
   ```
   coco/
       ├── annotations/
       ├── train2017/
       ├── val2017/
   ```

2. Train the YOLOv5 model on the COCO dataset:
   ```bash
   python train.py --img 640 --batch 16 --epochs 50 --data coco.yaml --weights yolov5s.pt
   ```

   **Parameters**:
   - `--img`: Image size used during training.
   - `--batch`: Batch size.
   - `--epochs`: Number of epochs to train.
   - `--data`: Path to `coco.yaml` file which includes dataset details.
   - `--weights`: Path to pretrained weights (you can start with `yolov5s.pt` for small models).

3. After training, the model weights will be saved under `runs/train/exp/weights`.

## Object Detection with Trained Model

### Detect Objects in Images

Use the following command to run object detection on a single image:

```bash
python detect.py --source path/to/image.jpg --weights runs/train/exp/weights/best.pt --img 640 --conf 0.4
```

**Parameters**:
- `--source`: Path to the input image.
- `--weights`: Path to the trained model weights.
- `--img`: Image size used for detection.
- `--conf`: Confidence threshold for detection (objects with lower confidence are ignored).

The output will be saved in the `runs/detect/exp` folder.

### Detect Objects in Videos

Use the following command to detect objects in a video:

```bash
python detect.py --source path/to/video.mp4 --weights runs/train/exp/weights/best.pt --img 640 --conf 0.4
```

**Parameters**:
- `--source`: Path to the input video file.
- `--weights`: Path to the trained model weights.
- `--img`: Image size used for detection.
- `--conf`: Confidence threshold for detection.

The result will be a video saved in the `runs/detect/exp` folder with detected objects.

## Result Visualization

- The detected objects in images and videos will be displayed with bounding boxes and confidence scores.
- Results will be saved in the `runs/detect/exp` directory by default.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

- **YOLOv5** by Ultralytics ([GitHub Repository](https://github.com/ultralytics/yolov5))
- **COCO Dataset** ([Website](http://cocodataset.org))

---
