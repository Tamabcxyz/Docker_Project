# Python libs supported
### Datasets
```
datasets: Hugging Face's dataset loading/processing library — works great with transformers.
chardet: Character encoding detection (useful when loading multilingual datasets).
```
### Numerical & Signal Processing
```
numpy: Core numerical array processing.
scipy: Scientific computing — signal processing, FFT, filters, etc.
Cython: Compiles Python-like code into C for speed.
einops: Elegant tensor ops for rearranging and composing tensor dimensions.
lpips: Perceptual similarity metric used for comparing images (especially in generative models).
```
### Audio Processing & Speech
```
librosa: Audio analysis — spectrograms, MFCCs, pitch, beat tracking.
pydub: Audio editing, conversion, and manipulation.
phonemizer: Converts text to phonemes (for TTS preprocessing).
piper-tts: Lightweight, fast TTS engine based on Larynx/VITS.
# piper-phonemize / piper_phonemize: Phoneme conversion library used with Piper.
textgrid: Reads/writes Praat .TextGrid files (used in phonetic alignments).
```
### Deep Learning & Transformers
```
torch: PyTorch core library (DL framework).
torchvision: Image utilities, pretrained models, transforms (for vision tasks).
torchaudio: Audio processing library in PyTorch.
torchtext: Text data utilities for NLP with PyTorch.
torchmetrics: PyTorch-based evaluation metrics.
pytorch-lightning: High-level PyTorch wrapper for cleaner training loops and reproducibility.
transformers: Hugging Face's library for pretrained models (BERT, GPT, T5, etc.).
diffusers: Hugging Face's library for diffusion models like Stable Diffusion.
trl: Transformers Reinforcement Learning — fine-tune language models with reward models (e.g., RLHF).
accelerate: Simplifies PyTorch training on multi-GPU/TPU setups.
hf_transfer: Tooling for faster model downloads from Hugging Face Hub (e.g., via torrent, mirror, etc.).
```
### Inference & Optimization
```
bitsandbytes: 8-bit optimizers and quantization — helps run large models with less memory (often used with LLMs).
onnxruntime / onnxruntime-gpu: Run models exported to ONNX format — allows for inference on CPU or GPU, independent of PyTorch/TensorFlow.
ffmpeg / ffmpeg-python: Audio/video encoding, decoding, conversion, and filtering.
```
### Visualization & Monitoring
```
matplotlib: Plotting and visualization.
tensorboard: TensorFlow/PyTorch-compatible tool for visualizing training logs, metrics, graphs.
```
### Media & Face
```
mediapipe==0.8.11: Google’s framework for hand, face, pose, and object tracking (real-time computer vision).
yt-dlp: YouTube video downloader (supports more formats and fixes compared to youtube-dl).
```

```
root@79dae132c44f:/# pip list --format=columns
Package                      Version
---------------------------- -----------
absl-py                      2.2.2
accelerate                   0.33.0
aiohappyeyeballs             2.4.4
aiohttp                      3.10.11
aiosignal                    1.3.1
astunparse                   1.6.3
async-timeout                5.0.1
attrs                        25.3.0
audioread                    3.0.1
babel                        2.17.0
beautifulsoup4               4.13.4
bitsandbytes                 0.45.0
blinker                      1.8.2
Brotli                       1.1.0
cachetools                   5.5.2
certifi                      2025.1.31
cffi                         1.17.1
chardet                      5.2.0
charset-normalizer           3.4.1
click                        8.1.8
colorama                     0.4.6
coloredlogs                  15.0.1
contourpy                    1.1.1
csvw                         3.5.1
cycler                       0.12.1
Cython                       3.0.12
datasets                     3.1.0
decorator                    5.2.1
deepface                     0.0.93
diffusers                    0.33.1
dill                         0.3.8
dlib                         19.24.6
dlinfo                       1.2.1
docstring_parser             0.16
einops                       0.8.1
eval_type_backport           0.2.2
face-recognition             1.3.0
face_recognition_models      0.3.0
ffmpeg-python                0.2.0
filelock                     3.16.1
fire                         0.7.0
Flask                        3.0.3
Flask-Cors                   5.0.0
flatbuffers                  25.2.10
fonttools                    4.57.0
frozenlist                   1.5.0
fsspec                       2024.9.0
future                       1.0.0
gast                         0.4.0
gdown                        5.2.0
google-auth                  2.39.0
google-auth-oauthlib         0.4.6
google-pasta                 0.2.0
grpcio                       1.70.0
gunicorn                     23.0.0
h5py                         3.11.0
hf_transfer                  0.1.9
huggingface-hub              0.30.2
humanfriendly                10.0
idna                         3.10
importlib_metadata           8.5.0
importlib_resources          6.4.5
isodate                      0.7.2
itsdangerous                 2.2.0
jax                          0.4.13
Jinja2                       3.1.6
joblib                       1.4.2
jsonschema                   4.23.0
jsonschema-specifications    2023.12.1
keras                        2.11.0
Keras-Applications           1.0.8
keras-vggface                0.6
kiwisolver                   1.4.7
language-tags                1.2.0
lazy_loader                  0.4
libclang                     18.1.1
librosa                      0.11.0
lightning-utilities          0.11.9
llvmlite                     0.41.1
lpips                        0.1.4
Markdown                     3.7
markdown-it-py               3.0.0
MarkupSafe                   2.1.5
matplotlib                   3.7.5
mdurl                        0.1.2
mediapipe                    0.10.10
ml-dtypes                    0.2.0
mpmath                       1.3.0
msgpack                      1.1.0
mtcnn                        0.1.1
multidict                    6.1.0
multiprocess                 0.70.16
mutagen                      1.47.0
numba                        0.58.1
numpy                        1.24.4
oauthlib                     3.2.2
onnxruntime                  1.19.2
onnxruntime-gpu              1.19.2
opencv-contrib-python        4.11.0.86
opencv-python                4.11.0.86
opt_einsum                   3.4.0
packaging                    24.2
pandas                       2.0.3
phonemizer                   3.3.0
pillow                       10.4.0
pip                          25.0.1
piper_phonemize              1.2.0
pkgutil_resolve_name         1.3.10
platformdirs                 4.3.6
pooch                        1.8.2
propcache                    0.2.0
protobuf                     3.19.6
psutil                       7.0.0
pyarrow                      17.0.0
pyasn1                       0.6.1
pyasn1_modules               0.4.2
pycparser                    2.22
pycryptodomex                3.22.0
pydub                        0.25.1
Pygments                     2.19.1
pyparsing                    3.1.4
PySocks                      1.7.1
python-dateutil              2.9.0.post0
pytorch-lightning            2.0.9.post0
pytz                         2025.2
PyYAML                       6.0.2
rdflib                       7.1.4
referencing                  0.35.1
regex                        2024.11.6
requests                     2.32.3
requests-oauthlib            2.0.0
retina-face                  0.0.17
rfc3986                      1.5.0
rich                         14.0.0
rpds-py                      0.20.1
rsa                          4.9.1
safetensors                  0.5.3
scikit-learn                 1.3.2
scipy                        1.10.1
segments                     2.3.0
setuptools                   75.3.2
shtab                        1.7.2
six                          1.17.0
sounddevice                  0.5.1
soundfile                    0.13.1
soupsieve                    2.6
soxr                         0.3.7
sympy                        1.13.3
tensorboard                  2.11.2
tensorboard-data-server      0.6.1
tensorboard-plugin-wit       1.8.1
tensorflow                   2.11.0
tensorflow-estimator         2.11.0
tensorflow-io-gcs-filesystem 0.34.0
termcolor                    2.4.0
TextGrid                     1.6.1
threadpoolctl                3.5.0
tokenizers                   0.20.3
torch                        1.11.0
torchaudio                   0.11.0
torchmetrics                 0.11.4
torchtext                    0.12.0
torchvision                  0.12.0
tqdm                         4.67.1
transformers                 4.46.3
trl                          0.11.4
typeguard                    4.4.0
typing_extensions            4.13.2
tyro                         0.9.18
tzdata                       2025.2
Unidecode                    1.3.8
uritemplate                  4.1.1
urllib3                      2.2.3
websockets                   13.1
Werkzeug                     3.0.6
wheel                        0.45.1
wrapt                        1.17.2
xxhash                       3.5.0
yarl                         1.15.2
yt-dlp                       2024.10.22
zipp                         3.20.2
```

# create Dockerfile
```
FROM python:3.8-slim

RUN python --version

# System dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    cmake \
    git \
    g++ \
    wget \
    curl \
    ffmpeg \
    libsm6 \
    libxext6 \
    libxrender-dev \
    libglib2.0-0 \
    libgtk2.0-dev \
    libboost-all-dev \
    libopenblas-dev \
    liblapack-dev \
    autoconf \
    automake \
    libtool \
    pkg-config \
    && rm -rf /var/lib/apt/lists/*

# Upgrade pip
RUN pip install --upgrade pip==25.0.1 setuptools wheel

# Core ML & Utility libraries
# internal libs
RUN pip install --no-cache-dir \
numpy>=1.19.0 \
pandas \
requests \
flask \
pillow \
matplotlib \
scipy \
scikit-learn \
opencv-python \
opencv-contrib-python \
dlib \
face-recognition \
tensorflow==2.11.0 \
keras-vggface \
keras-applications \
    deepface \
    torch==1.11.0 \
    torchvision==0.12.0 \
    torchaudio==0.11.0 \
    torchmetrics==0.11.4 \
    torchtext==0.12.0 \
    pytorch-lightning \
    tensorboard \
    accelerate==0.33.0 \
    bitsandbytes \
    trl \
    diffusers \
    transformers \
    hf_transfer \
    chardet \
    einops \
    lpips \
    textgrid \
    Unidecode \
    Cython>=0.29.0 \
    librosa>=0.9.2 \
    phonemizer \
    pydub \
    ffmpeg-python \
    mediapipe==0.10.10 \
    onnxruntime \
    onnxruntime-gpu \
    datasets \
    yt-dlp
    
# external libs
# Build espeak-ng from source (latest version with needed functions)
RUN git clone https://github.com/espeak-ng/espeak-ng.git /opt/espeak-ng && \
    cd /opt/espeak-ng && \
    ./autogen.sh && \
    ./configure --prefix=/usr && \
    make -j$(nproc) && \
    make install


# Install ONNX Runtime C++ SDK
RUN curl -L https://github.com/microsoft/onnxruntime/releases/download/v1.16.3/onnxruntime-linux-x64-1.16.3.tgz | tar xz && \
    mkdir -p /opt/onnxruntime && \
    mv onnxruntime-linux-x64-1.16.3/* /opt/onnxruntime

ENV ONNXRUNTIME_DIR=/opt/onnxruntime
RUN git clone https://github.com/rhasspy/piper-phonemize.git /tmp/piper-phonemize && \
    CXXFLAGS="-I$ONNXRUNTIME_DIR/include" \
    LDFLAGS="-L$ONNXRUNTIME_DIR/lib" \
    pip install /tmp/piper-phonemize && \
    rm -rf /tmp/piper-phonemize


# Download and install piper_tts from wheel
# RUN wget --no-check-certificate https://files.pythonhosted.org/packages/24/aa/215bced0725cf5b5afe939f86b177c8ddb0d38292a94e85c55b3fcf6d46d/piper_tts-1.2.0-py3-none-any.whl -O /tmp/piper_tts-1.2.0-py3-none-any.whl \
#     && pip install /tmp/piper_tts-1.2.0-py3-none-any.whl \
#     && rm /tmp/piper_tts-1.2.0-py3-none-any.whl


```
# Build image
```
cd Docker_ai
docker build -t ai_base .
```

# Run a container base on the image
```
docker run -it ai_base /bin/bash
```

# Add tag amd push to docker hub
```
docker tag ai_base tamabcxyz/ai_base:v1
docker login
docker push tamabcxyz/ai_base:v1
```

# Pull public image from Docker hub
```
docker pull tamabcxyz/ai_base:v1
```