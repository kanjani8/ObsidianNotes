 WSL2(Windows10-Ubuntu18) 상에서
 
 python -m venv ./env  실행으로 가상환경 생성할 때
 
 ##### Error: Command '['/home/minji/privateGPT/env/bin/python3.8', '-Im', 'ensurepip', '--upgrade', '--default-pip']' returned non-zero exit status 1.
 
 에러 발생.
원인: https://dev.classmethod.jp/articles/python-venv-error/

 오랜만에 python 사용이 이유인 듯 하여 3.11 버전으로 다시 깔기로 했음. 사유: Langchain이랑 맞춰서 겸사겸사 버전 충돌을 최소화 하기 위함.


그래서 기존의 Python을 제거하기로 했는데, 

python --version이랑 python3 --version의 결과 버전이 다른 문제 발생
https://stackoverflow.com/questions/76517911/the-output-of-python-version-and-python3-version-are-not-the-same?newreg=cf3a2245d29841dd8b60e14f316cff25

