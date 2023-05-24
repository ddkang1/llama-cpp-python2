```shell
wget https://repo.anaconda.com/miniconda/Miniconda3-py39_23.3.1-0-Linux-x86_64.sh
bash Miniconda3-py39_23.3.1-0-Linux-x86_64.sh
conda create --name LLM python=3.9 -y
conda activate LLM
conda install -c conda-forge gcc=9 gxx_linux-64=9 libgcc-ng

git clone https://github.com/abetlen/llama-cpp-python.git
cd llama-cpp-python

CMAKE_ARGS="-DLLAMA_CUBLAS=on" FORCE_CMAKE=1 pip install llama-cpp-python
CMAKE_ARGS="-DLLAMA_CUBLAS=on" FORCE_CMAKE=1 pip install llama-cpp-python[server]

HOST=0.0.0.0 PORT=8080 python3 -m llama_cpp.server --model /home/ec2-user/models/Manticore-13B.ggmlv3.q8_0.bin --n_gpu_layers 40 --n_ctx 2048 --verbose
HOST=0.0.0.0 PORT=8080 python3 -m llama_cpp.server --model /home/ec2-user/models/WizardLM-30B-Uncensored.ggmlv3.q5_1.bin --n_gpu_layers 50

```