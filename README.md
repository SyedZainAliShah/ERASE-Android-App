# ERASE — On-Device Trash Detection

An Android app that detects and classifies waste in photos — plastic, paper, metal, and more — to help users sort trash correctly and promote recycling. A custom-trained object detection model runs **fully on-device** via TensorFlow Lite: no network connection or cloud API needed.

## How It Works

1. Snap a photo with the in-app camera (or use a sample image)
2. The TFLite `ObjectDetector` runs inference on the bitmap
3. Detected items are drawn with bounding boxes and class labels directly on the image

## Model

- **Custom dataset**: 5,000+ self-collected and annotated images of real-world waste
- **Training**: YOLOv4-based detector, converted to TensorFlow Lite for mobile inference
- **Accuracy**: ~92% across 5 waste categories
- End-to-end ownership: data collection → labeling → training → conversion → Android deployment

## Tech Stack

| Component | Technology |
| --- | --- |
| App | Kotlin, Android SDK |
| Inference | TensorFlow Lite Task Library (`ObjectDetector`) |
| Model | YOLOv4 → TFLite (`gen.tflite` in `app/src/main/assets/`) |
| Image handling | Camera intent, EXIF-aware rotation, canvas overlay for results |

## Getting Started

1. Clone the repo and open in Android Studio
2. Build and run on a device or emulator (camera recommended on a real device)
3. Take a photo — detections render with boxes and labels

## Swapping the Model

Replace `app/src/main/assets/gen.tflite` with any TFLite object-detection model and update the filename in `MainActivity.kt`.

## Housekeeping Note

The `app/build/` directory is currently committed to the repo — it's generated output and safe to delete. Add `build/` and `app/build/` to `.gitignore` to keep the repo lean.

---

Built by [@SyedZainAliShah](https://github.com/SyedZainAliShah)
