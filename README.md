# llamacpp-langchain-neuralbeagle-demo

a small demo repo to show how I got neuralbeagle14-7b running locally on my 8GB GPU

__See [demo.ipynb](./demo.ipynb)__

# Summary

This notebook will demonstrate the process I went through to run `neuralbeagle14-7b` on my laptop's 8GB GPU in Windows, as seen in [my LinkedIn post from January 27th, 2024](https://www.linkedin.com/posts/jsundance_free-local-private-ai-on-my-laptop-thanks-activity-7157117360728862720-MWxn?utm_source=share&utm_medium=member_desktop). It pulls heavily from [this LangChain documentation](https://python.langchain.com/docs/integrations/llms/llamacpp).

I was able to use `llama-cpp-python` _without_ my GPU, and it took me a couple installs before it was really loading all of the layers onto the GPU. It was still fast without the GPU, but that's not the point. ;)

I'm using an NVIDIA RTX A4000 laptop GPU. I will be compiling `llama-cpp-python` instead of using the "usual" `pip install` because I _think_ this is a more reliable method. I will be using the cuBLAS backend, but you can use other backends for AMD or Apple or whatever (more or this later).

I will also describe an issue I had with a missing dll, and offer troubleshooting advice for that.

Joshua Bailey #LearningInPublic January 28, 2024


# tldr for users with conda and cuda 11.8:

```cmd
mkdir neuralbeagle && cd neuralbeagle
conda create -n neuralbeagle python=3.11
conda activate neuralbeagle

python -m pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118

set CMAKE_ARGS=-DLLAMA_CUBLAS=on
set FORCE_CMAKE=1
python -m pip install -v --upgrade --force-reinstall --no-cache-dir llama-cpp-python
```

# TODO
- [ ] make a todo list
