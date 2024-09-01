

# Animatediff-Cli-Android-Termux
gradio apps don't work u get crash every time it loads unet:(


pkg updated && pkg upgrade -y && termux-setup-storage && pkg install wget -y && pkg install git -y && pkg install proot -y && cd ~ && git clone https://github.com/MFDGaming/ubuntu-in-termux.git && cd ubuntu-in-termux && chmod +x ubuntu.sh && ./ubuntu.sh -y && ./startubuntu.sh

Installing ComfyUI Run below commands sequentially as root user in Ubuntu
Install basic tools

apt update && apt upgrade -y && apt-get install curl git gcc make build-essential python3 python3-dev python3-distutils python3-pip python3-venv python-is-python3 -y && pip install ffmpeg && apt dist-upgrade -y && apt install wget && apt-get install libgl1 libglib2.0-0 libsm6 libxrender1 libxext6 -y && apt-get install google-perftools &&
apt install libgoogle-perftools-dev

git clone https://github.com/neggles/animatediff-cli

cd animatediff-cli

python3.10 -m venv .venv

source .venv/bin/activate


python -m pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118


python -m pip install -e '.[dev]'


python -m pip install --upgrade transformers==4.33.0


animatediff --help


