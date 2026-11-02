# VisionGuard

A set of 19 standalone computer vision modules for surveillance, safety, crowd analytics and human-computer interaction, built on YOLO detection and tracking, pose estimation, MediaPipe and classical OpenCV. Each module lives in its own folder with its own script, `README.md` and `requirements.txt`, so you can use the whole repo or just one folder.

Maintained by **Aditya Singh Thakur** ([@AdityaST93](https://github.com/AdityaST93)).

> **Attribution:** VisionGuard is adapted from [YOLO_Projects](https://github.com/Nawaf-Rayhan585/YOLO_Projects) by Nawaf Rayhan, released under the MIT License. The original copyright notice is kept in [`LICENSE`](LICENSE).

---

## Modules

### Security & Safety
| Module | What it does |
|---|---|
| [zone-breach-alert](zone-breach-alert) | Raises an alert when a person's feet enter a restricted zone |
| [anomaly-pose-detector](anomaly-pose-detector) | Pose-based heuristic that flags crouching combined with fast hand movement |
| [fire-smoke-alarm](fire-smoke-alarm) | Real-time fire detection with an alarm, plus a training notebook |
| [fall-alert](fall-alert) | Flags a sudden drop into a horizontal posture |
| [ppe-compliance-check](ppe-compliance-check) | Flags missing hard hats, safety vests and masks |
| [driver-fatigue-monitor](driver-fatigue-monitor) | Eye-closure and yawn detection for driver monitoring |
| [privacy-face-masker](privacy-face-masker) | Blurs or pixelates every face in a feed for privacy compliance |
| [rodent-watch](rodent-watch) | Rodent detection with a sighting log, plus a training notebook |

### Crowd & Retail Analytics
| Module | What it does |
|---|---|
| [footfall-counter](footfall-counter) | IN/OUT footfall counting with a live dashboard |
| [crowd-density-monitor](crowd-density-monitor) | Live crowd density heatmap and person count |
| [queue-time-tracker](queue-time-tracker) | Live queue length and rolling average wait time |
| [parking-slot-monitor](parking-slot-monitor) | Per-slot free/occupied detection for a parking lot |

### Traffic & Vehicles
| Module | What it does |
|---|---|
| [vehicle-tracker](vehicle-tracker) | Multi-class vehicle detection with persistent tracking IDs |
| [plate-reader-anpr](plate-reader-anpr) | Number plate detection and OCR, plus a training notebook |

### Human-Computer Interaction
| Module | What it does |
|---|---|
| [attention-monitor](attention-monitor) | Self-monitoring distraction guard with full-screen alerts |
| [handedness-detector](handedness-detector) | Labels each detected hand as Left or Right |
| [gesture-volume](gesture-volume) | Pinch-gesture system volume control |

### Document & Vision Utilities
| Module | What it does |
|---|---|
| [doc-scan-reader](doc-scan-reader) | Document edge detection, perspective correction and OCR |
| [background-swap](background-swap) | Background blur or replacement using instance segmentation |

---

## Tech stack

- **Detection & tracking:** Ultralytics YOLO (v8/v11), ByteTrack via `supervision`
- **Pose & hands:** YOLO-Pose, MediaPipe, cvzone
- **Segmentation:** YOLO-Seg
- **OCR:** EasyOCR, Tesseract
- **Core:** Python, OpenCV, NumPy
- **Training:** Google Colab notebooks with Roboflow datasets, for modules that need a custom model

## Installation

Each module is self-contained. Clone the repo and install only what you need:

```bash
git clone https://github.com/AdityaST93/VisionGuard.git
cd VisionGuard/<module-folder>
pip install -r requirements.txt
```

## Usage

Every script takes a `--source` argument (a video path, an image path, or a webcam index) plus module-specific flags. See each folder's `README.md` for exact options.

```bash
python <script>.py --source your_video.mp4
python <script>.py --source 0   # webcam
```

## Ready-to-run vs. train-first

- **Ready to run:** most modules use a general-purpose pretrained YOLO or MediaPipe model and work right after `pip install`.
- **Train first:** fire, rodent, license plate and PPE detection need a domain-specific model. Those folders include a Colab notebook (`train_*_model.ipynb`) and a local inference script.

No datasets or trained weights are committed. Point `--source` and `--model` at your own.

## License

MIT. See [`LICENSE`](LICENSE).
