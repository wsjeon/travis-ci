# Header
Bootstrap: shub
From: wsjeon/singularity-development-setting:zsh

# Section
%post
    # Ray rllib
    apt-get install -y libxrender1
    pip install --progress-bar off psutil
    pip install --progress-bar off -U https://s3-us-west-2.amazonaws.com/ray-wheels/latest/ray-0.8.0.dev1-cp36-cp36m-manylinux1_x86_64.whl
    pip install --progress-bar off requests

    # PyTorch
    pip install --progress-bar off https://download.pytorch.org/whl/cu100/torch-1.1.0-cp36-cp36m-linux_x86_64.whl
    pip install --progress-bar off https://download.pytorch.org/whl/cu100/torchvision-0.3.0-cp36-cp36m-linux_x86_64.whl

    # # SMAC
    # git clone https://github.com/oxwhirl/smac.git /SMAC
    # pip install /SMAC

    # # StarCraftII
    # mkdir -p /StarCraftII
    # export SC2PATH=/StarCraftII
    # wget -q -O SC2.zip http://blzdistsc2-a.akamaihd.net/Linux/SC2.4.7.1.zip
    # unzip -qq -P iagreetotheeula SC2.zip
    # rm -rf SC2.zip

    # # SMAC maps
    # mkdir -p $SC2PATH/Maps
    # ln -s /SMAC/smac/env/starcraft2/maps/SMAC_Maps $SC2PATH/Maps

    # Multi-agent particle environments
    git clone https://github.com/wsjeon/multiagent-particle-envs.git /MPE
    cd /MPE
    pip install --progress-bar off -e .

    # MADDPG
    git clone https://github.com/openai/maddpg.git /maddpg
    cd /maddpg
    pip install --progress-bar off -e .

    # Dependencies
    pip install --progress-bar off opencv-python
    pip install --progress-bar off pandas
    pip install --progress-bar off lz4
    pip install --progress-bar off setproctitle

%environment
    # export SC2PATH=/StarCraftII
    export SHELL=/bin/zsh

%runscript
    mkdir -p /tmp_log/ray_results
    ln -sf /tmp_log/ray_results ~/ray_results
    exec /bin/zsh "$@"
