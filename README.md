!git clone https://github.com/ultralytics/yolov5.git
%cd yolov5
!pip install -r requirements.txt
!pip install -q ultralytics
!wget https://github.com/ultralytics/yolov5/releases/download/v7.0/yolov5s.pt
!pwd

from google.colab import files
uploaded = files.upload()

import cv2
import torch
from PIL import Image
import numpy as np
from google.colab import files
from IPython.display import display, Video
import os

device = 'cuda' if torch.cuda.is_available() else 'cpu'

model = torch.hub.load('ultralytics/yolov5', 'yolov5s', pretrained=True).to(device)

uploaded = files.upload()

if uploaded:
    video_path = next(iter(uploaded))
    print(f"업로드된 파일 이름: {video_path}")
else:
    raise ValueError("업로드된 파일이 없습니다. 다시 시도해주세요.")

cap = cv2.VideoCapture(video_path)

output_path = '자동차영상.mp4'
fourcc = cv2.VideoWriter_fourcc(*'mp4v')
fps = cap.get(cv2.CAP_PROP_FPS)
width  = int(cap.get(cv2.CAP_PROP_FRAME_WIDTH))
height = int(cap.get(cv2.CAP_PROP_FRAME_HEIGHT))
out = cv2.VideoWriter(output_path, fourcc, fps, (width, height))

while cap.isOpened():
    ret, frame = cap.read()
    if not ret:
        break

    results = model(frame)

    annotated_frame = results.render()[0]

    out.write(annotated_frame)

cap.release()
out.release()
cv2.destroyAllWindows()

from google.colab import files
files.download('자동차영상.mp4')
