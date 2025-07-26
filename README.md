# 0716 과제3 - 차량 추적 및 속도/방향 분석 시스템

- 프로젝트 설명 :

이 프로젝트는 비디오 내에서 밝은 객체(예: 차량 등)를 감지하여 각 객체의 위치, 속도(m/s), 이동 방향(°)을 추적하고 시각화하는 간단한 트래킹 시스템입니다.  
센트로이드 기반의 추적 알고리즘(Centroid Tracker)을 활용하여 각 객체의 ID를 유지하며, 프레임 간 위치 변화를 바탕으로 속도와 방향을 계산합니다.

- 사용법
1. Google Colab에서 코드를 실행합니다.
2. 실행 시 나타나는 파일 업로드 창에서 처리할 동영상을 업로드합니다.
3. 영상 내 밝은 객체가 감지되고, 각 객체의 ID / 속도 / 방향이 영상에 표시됩니다.
4. 분석된 결과 영상 output_final.mp4가 자동으로 다운로드됩니다.


- 설치 방법
Google Colab 환경을 기준으로 다음 라이브러리가 필요합니다:

```python
import cv2
import numpy as np
from math import atan2, degrees, sqrt
from google.colab import files
```

# 0726 과제4 - 차량 추적 및 충돌 예측 시스템


##  프로젝트 설명
영상 속 차량을 추적하여 이동 경로와 속도를 계산하고, 차량 간의 충돌 시간을 예측합니다.  
충돌 예상 시간이 2초 이하일 경우 경고 로그를 출력하며, 결과 영상을 생성합니다.

##  사용법
1. Google Colab에서 코드 실행  
2. 분석할 차량 영상 업로드  
3. 실행 완료 후 아래 두 파일 다운로드  
   - `collision_warning_output.mp4` : 결과 영상  
   - `collision_log.txt` : 충돌 경고 로그

##  설치 방법

```python
import cv2
import numpy as np
from math import atan2, degrees, sqrt
from google.colab import files
