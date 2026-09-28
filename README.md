# ctdt

Computer vision demo for detecting eye blinks as a proxy signal for drowsiness, using facial landmarks and the eye-aspect-ratio (EAR) technique.

This repository includes:
- `detect_blinks.py`: runs realtime blink detection from a webcam (and can be adapted for video input).
- `shape_predictor_68_face_landmarks.dat`: a pretrained facial landmark model used by `dlib`.

> Note: The current script defaults to webcam input (`VideoStream(src=0)`), even though it contains commented examples for processing a video file.

## Prerequisites

- Python 3.x
- A working webcam (for the default realtime mode)
- System packages needed to build/install `dlib` (varies by OS)

Python dependencies (installed via `pip`):
- `numpy`, `scipy`
- `opencv-python` (cv2)
- `dlib`
- `imutils`

## Installation

Clone the repo:

```bash
git clone https://github.com/Abishek10/ctdt.git
cd ctdt
```

Create and activate a virtual environment (recommended):

```bash
python -m venv .venv
source .venv/bin/activate  # macOS/Linux
# .venv\Scripts\activate   # Windows (PowerShell)
```

Install dependencies:

```bash
pip install -U pip
pip install numpy scipy opencv-python imutils dlib
```

## Quickstart (webcam)

Run blink detection using the included facial landmark model:

```bash
python detect_blinks.py \
  --shape-predictor shape_predictor_68_face_landmarks.dat
```

Expected behavior:
- A window named **Frame** opens.
- The script draws contours around both eyes and overlays:
  - `Blinks: <count>`
  - `EAR: <value>`
- Press `q` to quit.

## Usage

`detect_blinks.py` arguments:

- `-p, --shape-predictor` (required): path to the facial landmark predictor `.dat` file.
- `-v, --video` (optional): path to an input video file.

### Video input

The script contains an example for video input in the header comment, but currently the implementation starts a webcam stream by default.

If you want to process a video file, you can adapt the code to use `FileVideoStream` and set `fileStream = True`.

## Project structure

- `detect_blinks.py` — main blink detection script.
- `shape_predictor_68_face_landmarks.dat` — facial landmark model used by `dlib.shape_predictor`.
- `README.md` — project documentation.

## Contributing

Issues and PRs are welcome.

If you submit a PR:
- keep changes focused
- include a short description of how you tested (OS + Python version)

## License

No license file is currently present in the repository. If you intend others to reuse this code, consider adding a LICENSE file (e.g., MIT, Apache-2.0).