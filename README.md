# DeFakeIt — AI Deepfake Detector

A browser-based deepfake detection tool built with React and TensorFlow.js. Uses a trained neural network to classify faces as real or AI-generated with confidence scoring. All inference runs **client-side** — no backend or server required.

## Features

- **Live Webcam Detection** — real-time frame-by-frame analysis using your camera
- **Image Upload** — drag & drop or browse to analyze static images (JPG, PNG, WebP up to 10MB)
- **Confidence Scoring** — displays real vs. fake probability with certainty level (Low / Medium / High / Very High)
- **Processing Stats** — shows frame count and per-frame processing time in milliseconds
- **Privacy First** — no data ever leaves your device; everything runs in the browser

## Tech Stack

- [React 19](https://react.dev/)
- [TensorFlow.js](https://www.tensorflow.org/js) — client-side ML inference
- [Tailwind CSS](https://tailwindcss.com/) — utility-first styling
- [Font Awesome](https://fontawesome.com/) — icons

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) v18 or higher
- npm

### Installation

```bash
git clone https://github.com/Pranshu0722/DeFakeIt.git
cd DeFakeIt
npm install
```

### Run Locally

```bash
npm start
```

Opens at [http://localhost:3000](http://localhost:3000).

### Build for Production

```bash
npm run build
```

Output goes to the `build/` folder, ready for deployment.

## How It Works

1. The app loads a pre-trained TensorFlow.js model from the `public/model/` directory on startup.
2. For webcam mode, frames are captured and preprocessed to 224×224 pixels, normalized, and fed to the model every ~100ms.
3. For image uploads, the image is drawn onto a canvas, resized to 224×224, and passed through the same pipeline.
4. The model outputs two class probabilities — **Class 0 (Real)** and **Class 1 (Fake)** — which are displayed with confidence metrics.

## Project Structure

```
src/
├── App.js          # Main detector component (model loading, webcam, inference)
├── InstallAlert.js # PWA install prompt
├── App.css         # Global styles
└── index.js        # Entry point

public/
└── model/          # TensorFlow.js model files (model.json + weights)
```

## License

MIT
