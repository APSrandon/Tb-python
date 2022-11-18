# Tb-python
Trabalho sobre o python

Universidade do Vale do Itajaí
Escola do Mar, Ciência e Tecnologia
Professor Felipe Viel
Aluno André Poite da Silva
Curso Ciências da Computação


import cv2
import numpy as np
import matplotlib.pyplot as plt
#caso for usar o Google Colab com a OpenCV, usar a lib abaixo
from google.colab.patches import cv2_imshow  

A parte do código acima são as bibliotecas para fazer com que o código funcione corretamente, sem elas o código não funciona.
Elas seram fundamentais para que as alterações nas imagens sejam feitas.

As demais partes do codigo serão responsaveis por fazer as alterações, como poderão ser vistas nas proximas partes do código.

#abrir a imagem
img = cv2.imread('t1.jpg',1)
#caso for usar o Google Colab com a OpenCV,
cv2_imshow(img)

Esse código ficar responsável por abrir à imagem para ver se e imagem correta.
Com a imagem conferida entra o proximo estágio do código.

#aplicando conversão ponderada - converte imagem colorida para preto e branco
#img_grayscale_basic = 0.299*img[ : , : ,0] + 0.587*img[ : , : ,1] + 0.114*img[ : , : ,2]
#cv2
B, G, R = cv2.split(img)
img_grayscale_pondered = 0.299*B+0.587*G+0.114*R
img_grayscale_pondered = np.array(img_grayscale_pondered, dtype=np.uint8)
cv2_imshow(img_grayscale_pondered)

Nesse estágio do código por meio do uso da conceito conhecido mundialmente como, RGB faz com que um sequencia de números mude as cores de uma imagem digital,
o código acima faz com a imagem mude de cor deixando de ser colorida para se tornar preta e branca, mas isso não para so ai com esse mesmo codigo 
você pode alterar essa imagem para que ela fique de outras cores também, com tomalidades que puxem pro azul, vermelho, amarelo, verde ou roxo, 
todo vai depender pra qual finalidade você ultilizara esse codigo.

A Proxima parte do codigo mudar a imagem para negativa.

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

Nessa parte do codigo o conceito descrito acima e ultilizado para mudar os parametros da imagem à deixando negativa, com as suas cores opostas das originais.
Na proxima parte o brilho da imagem será mexido por meio de mais um codigo.

#contraste e brilho
img_in = cv2.imread('t1.jpg',0)
#altere os valores tanto de a quanto de b
a = -1 
b = 1
img_out = a*img_in + b
img_out = np.array(img_out, dtype = np.uint8)
cv2_imshow(img_in)
cv2_imshow(img_out)

Nessa parte do codigo a imagem e alterada para o preto e branco e depois tem o seu brilho diminuido ao maximo e em seguida aumentado também ao maximo,
para que a imagem tenha uma versão mais clara e outra mais escura.

Ja na ultima parte do codigo a imagem tem a sua nitidiz ou suavização mexida.

#suavização
#você pode ler sobre o conceito aqui: https://docs.opencv.org/4.x/d4/d13/tutorial_py_filtering.html
img_in = cv2.imread('t1.jpg',0)
kernel = np.ones((5,5),np.float32)/25
img_out_1 = cv2.filter2D(img_in,-1,kernel)
cv2_imshow(img_in)
cv2_imshow(img_out_1)

Nessa ultima parte do codigo a imagem teve a sua suavização mexida a deixando mas empasada que por fim também a deixa mas dificil de se inxergar.
