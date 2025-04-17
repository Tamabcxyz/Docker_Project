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


