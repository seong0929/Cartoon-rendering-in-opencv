# Cartoon-rendering-in-opencv

결과 사진
![image](https://user-images.githubusercontent.com/50050003/226864854-85b76f50-b833-437f-bddf-f2fe37f447ed.png)
![image](https://user-images.githubusercontent.com/50050003/226864872-78cfdc71-4796-40a1-bb2d-9ef49c86c2c7.png)
![image](https://user-images.githubusercontent.com/50050003/226864887-24288d94-47ee-4f0f-b265-904ce729a9fe.png)
![image](https://user-images.githubusercontent.com/50050003/226864904-f6200be2-3328-40cf-b370-4379b1c4d429.png)

<pre>
<code>
import cv2
import numpy as np
import matplotlib.pyplot as plt

#원본 이미지 로드 및 플로팅
img = cv2.imread("genshin.jpg")
img = cv2.cvtColor(img,cv2.COLOR_BGR2RGB)
plt.figure(figsize=(10,10))
plt.imshow(img)
plt.axis("off")
plt.title("Original Image")
plt.show()

#이미지를 그레이스케일로 변환
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
gray = cv2.medianBlur(gray, 5)
plt.figure(figsize=(10,10))
plt.imshow(gray,cmap="gray")
plt.axis("off")
plt.title("Grayscale Image")
plt.show()

#엣지 이미지 얻기
edges = cv2.adaptiveThreshold(gray, 255, cv2.ADAPTIVE_THRESH_MEAN_C, cv2.THRESH_BINARY, 9, 9)
plt.figure(figsize=(10,10))
plt.imshow(edges,cmap="gray")
plt.axis("off")
plt.title("Edged Image")
plt.show()

#이미지를 만화로 바꾸기
color = cv2.bilateralFilter(img, 9, 250, 250)
cartoon = cv2.bitwise_and(color, color, mask=edges)
plt.figure(figsize=(10,10))
plt.imshow(cartoon,cmap="gray")
plt.axis("off")
plt.title("Cartoon Image")
plt.show()
</code>
</pre>
