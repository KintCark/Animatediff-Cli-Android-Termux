# Animatediff-Cli-Android-Termux
I finally got animatediff cli to work on termux but u need 16 gb RAM as I'm still testing it on 12gb Ram phone.


pkg updated && pkg upgrade -y && termux-setup-storage && pkg install wget -y && pkg install git -y && pkg install proot -y && cd ~ && git clone https://github.com/MFDGaming/ubuntu-in-termux.git && cd ubuntu-in-termux && chmod +x ubuntu.sh && ./ubuntu.sh -y && ./startubuntu.sh

Installing ComfyUI Run below commands sequentially as root user in Ubuntu
Install basic tools

apt update && apt upgrade -y && apt-get install curl git gcc make build-essential python3 python3-dev python3-distutils python3-pip python3-venv python-is-python3 -y && pip install ffmpeg && apt dist-upgrade -y && apt install wget && apt-get install libgl1 libglib2.0-0 libsm6 libxrender1 libxext6 -y && apt-get install google-perftools &&
apt install libgoogle-perftools-dev

Install required extensions

apt-get install libgl1 libglib2.0-0 libsm6 libxrender1 libxext6 -y







git clone https://github.com/neggles/animatediff-cli

cd animatediff-cli

python3.10 -m venv .venv

source .venv/bin/activate

# install Torch. Use whatever your favourite torch version >= 2.0.0 is, but, good luck on non-nVidia...

python -m pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118

# install the rest of all the things (probably! I may have missed some deps.)

python -m pip install -e '.[dev]'


python -m pip install --upgrade transformers==4.33.0

# you should now be able to
animatediff --help

# There's a nice pretty help screen with a bunch of info that'll print here.


# There's a nice pretty help screen with a bunch of info that'll print here.

From here you'll need to put whatever checkpoint you want to use into data/models/sd, copy one of the prompt configs in config/prompts, edit it with your choices of prompt and model (model paths in prompt .json files are relative to data/, e.g. models/sd/vanilla.safetensors), and off you go.

Then it's something like (for an 8GB card):

animatediff generate --device cpu -c config/prompts/dreamshaper8.json -W 512 -H 512 -L 8 -C 8

You may have to drop -C down to 8 on cards with less than 8GB VRAM, and you can raise it to 20-24 on cards with more. 24 is max.

N.B. generating 128 frames is slow...





