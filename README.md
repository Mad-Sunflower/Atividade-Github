# Codigoremovercontrasteprofessor
import cv2
import numpy as np
import matplotlib.pyplot as plt
#caso for usar o Google Colab com a OpenCV, usar a lib abaixo
from google.colab.patches import cv2_imshow
#abrir a imagem
img = cv2.imread('t1.jpg',1)
#caso for usar o Google Colab com a OpenCV,
cv2_imshow(img)
#mostrando a imagem colorida - caso você use Python no seu computador
#reutilize para exibir as imagens em outros códigos
#Voce pode descomentar o código apagando as aspas simples
'''
cv2.imshow('in', img)
cv2.waitKey(0)
cv2.destroyAllWindows()
'''
#aplicando conversão ponderada - converte imagem colorida para preto e branco
#img_grayscale_basic = 0.299*img[ : , : ,0] + 0.587*img[ : , : ,1] + 0.114*img[ : , : ,2]

#cv2
B, G, R = cv2.split(img)
img_grayscale_pondered = 0.299*B+0.587*G+0.114*R

img_grayscale_pondered = np.array(img_grayscale_pondered, dtype=np.uint8)

cv2_imshow(img_grayscale_pondered)

#==============================================================================TRANSFORMAÇÕES

#negativo

#img_negative[ : , : ,0] = 255 - img[ : , : ,0]
#img_negative[ : , : ,1] = 255 - img[ : , : ,1]
#img_negative[ : , : ,2] = 255 - img[ : , : ,2]

#Mude a variavel colorida para 1 caso queira colorida, o para 0 caso queira em escala de cinza
colorida = 1
img_in = cv2.imread('t1.jpg',colorida)

img_out = 255 - img_in

cv2_imshow(img_in)
cv2_imshow(img_out)
#contraste e brilho
img_in = cv2.imread('t1.jpg',0)
#altere os valores tanto de a quanto de b

a = -1 
b = 1

img_out = a*img_in + b

img_out = np.array(img_out, dtype = np.uint8)

cv2_imshow(img_in)
cv2_imshow(img_out)

#==============================================================FILTRO ESPACIAL

#suavização
#você pode ler sobre o conceito aqui: https://docs.opencv.org/4.x/d4/d13/tutorial_py_filtering.html
img_in = cv2.imread('t1.jpg',0)

kernel = np.ones((5,5),np.float32)/25

img_out_1 = cv2.filter2D(img_in,-1,kernel)


cv2_imshow(img_in)
cv2_imshow(img_out_1)

