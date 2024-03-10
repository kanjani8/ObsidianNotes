



## 2023.11.19

[](https://github.com/kanjani8/.github.io/blob/main/README.md#20231119)

will be updated later. just for simple memo for now

To try segment anything model with unused laptop, and quick review [https://github.com/facebookresearch/segment-anything](https://github.com/facebookresearch/segment-anything)

1. check python installed with python --version
    
2. check Anaconda Powershell prompt installed
    
3. update anaconda with conda update -n base -c defaults conda
    
4. create a folder for this practice ./segmentAnything231119 and cd to this folder
    
5. install pytorch and torch vision with anaconda (cpu environment) [https://pytorch.org/get-started/locally/](https://pytorch.org/get-started/locally/) conda install pytorch torchvision torchaudio cpuonly -c pytorch
    
6. create virtual environment for python package management. python -m venv venv activate with venv\Scripts\activate.bat
    
    가상환경 내에서 패키지를 설치하려면, 가상환경을 활성화 한 상태에서 그냥 평소처럼 pip install로 패키지 설치를 하면 된다.
    
7. Install Segment Anything: pip install git+[https://github.com/facebookresearch/segment-anything.git](https://github.com/facebookresearch/segment-anything.git)
    
8. install optional packages for mask post-processing, saving masks in COCO format, the example notebooks, and exporting the model in ONNX format. pip install opencv-python pycocotools matplotlib onnxruntime onnx