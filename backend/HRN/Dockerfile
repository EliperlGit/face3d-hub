FROM nvidia/cuda:12.2.0-runtime-ubuntu22.04

ENV DEBIAN_FRONTEND=noninteractive
ENV TZ=Etc/UTC

RUN apt-get update && \
    apt-get install -y python3 python3-pip python3-dev python3-setuptools python3-opencv python3-numpy python3-scipy python3-pil.imagetk git curl libgl1-mesa-glx libglib2.0-0 && \
    rm -rf /var/lib/apt/lists/*

RUN python3 -m pip install --upgrade pip && \
    python3 -m pip install torch==2.1.0+cu121 torchvision==0.16.0+cu121 --index-url https://download.pytorch.org/whl/cu121

RUN python3 -m pip install --no-cache-dir --verbose -r requirements.txt

# Build PyTorch3D from source for PyTorch 1.13.1 + cu117
RUN python3 -m pip install pytorch3d -f https://dl.fbaipublicfiles.com/pytorch3d/packaging/wheels/py310_cu121_pyt210/download.html

# Install nvdiffrast
RUN git clone https://github.com/NVlabs/nvdiffrast.git && \
    cd nvdiffrast && python3 -m pip install . && cd .. && rm -rf nvdiffrast

WORKDIR /workspace
COPY . /workspace

CMD ["bash"]
