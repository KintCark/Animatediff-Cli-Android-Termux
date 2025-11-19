low vram mode is unsupported cause the required packages to run the animatediff are outdated I ran into to many problems this is the only way it can work. ima try again later. I. still working on. the mod




apt update -y && apt upgrade && apt install wget curl proot tar -y && wget https://raw.githubusercontent.com/AndronixApp/AndronixOrigin/master/Installer/Ubuntu22/ubuntu22.sh -O ubuntu22.sh && chmod +x ubuntu22.sh && bash ubuntu22.sh



apt update && apt upgrade -y && apt-get install curl git gcc make build-essential python3 python3-dev python3-distutils python3-pip python3-venv python-is-python3 -y && pip install ffmpeg && apt dist-upgrade -y && apt install wget && apt-get install libgl1 libglib2.0-0 libsm6 libxrender1 libxext6 -y && apt-get install google-perftools &&
apt install libgoogle-perftools-dev && pip install mediapipe && apt install libjpeg-dev libpng-dev

Install required extensions

apt-get install libgl1 libglib2.0-0 libsm6 libxrender1 libxext6 -y







How to use
I should write some more detailed steps, but here's the gist of it:

git clone https://github.com/neggles/animatediff-cli

cd animatediff-cli

'Fix' the issue with Python running in PRoot
export ANDROID_DATA=anything 

python3.10 -m venv .venv

source .venv/bin/activate

# install Torch. Use whatever your favourite torch version >= 2.0.0 is, but, good luck on non-nVidia...

pip install --no-cache-dir torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu pip install --no-cache-dir -r requirements.txt

pip uninstall transformers &&
python -m pip install --upgrade transformers==4.33.0


The error you're encountering is due to the split_torch_state_dict_into_shards function not being available in huggingface-hub version 0.20.3. This function is included starting from version 0.23.0.


To resolve this issue, update the huggingface-hub library to version 0.23.0 or later:

python -m pip install --upgrade huggingface-hub==0.23.0


you need diffusers 0.25.0

pip uninstall diffusers && pip install diffusers==0.25.0

do diffusers again and huggingface_hub fix after doing dev install


if you get bumpy not available error install older version of bumpy

pip uninstall numpy && pip install numpy==1.22.4

# install the rest of all the things (probably! I may have missed some deps.)

python -m pip install -e '.[dev]'

# you should now be able to

animatediff --help

# There's a nice pretty help screen with a bunch of info that'll print here.

From here you'll need to put whatever checkpoint you want to use into data/models/sd, copy one of the prompt configs in config/prompts, edit it with your choices of prompt and model (model paths in prompt .json files are relative to data/, e.g. models/sd/vanilla.safetensors), and off you go.

Then it's something like (for an 8GB card):

animatediff generate -c 'config/prompts/Absolute Reality16.json' -W 512 -H 512 -L 8 -C 8

You may have to drop -C down to 8 on cards with less than 8GB VRAM, and you can raise it to 20-24 on cards with more. 24 is max.

N.B. generating 128 frames is slow...



