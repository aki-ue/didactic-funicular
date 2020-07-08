import matplotlib
import numpy as np
import random
import cv2
"""
this code will create 200 images and 2 videos
interframe.avi is for interframe compression
innerframe.avi is for innerframe compression
"""

def YUV2RGB(yuv):
    ###yuv[:,:,1]+=128
    ###yuv[:,:,2]+=128
    for i in range(400):
        for j in range(400):
            yuv[i][j][1] -= 128
            yuv[i][j][2] -= 128

    m = np.array([[1.0, 1.0, 1.0],
                  [-0, -0.34, 1.772],
                  [1.4019, -0.7141380310058594, 0.00]])
    rgb = np.dot(yuv, m)
    return rgb

l=[]
for i in range(22,219,4):
    l.append(i)
random.shuffle(l)
im_y=[]
im_u=[]
im_v=[]
for i in range(400):
    im_u.append(l[i//8])
    im_u.append(l[i//8])
for i in range(400):
    im_v.append(l[i // 8])
    im_v.append(l[i // 8])
for i in range(20,220):
    im_y.append(i)
    im_y.append(i)
random.shuffle(im_y)
imagearray = np.zeros((400,400,3))
for i in range(400):
    for j in range(400):
        imagearray[j][i][0]=im_y[j]
        imagearray[i][j][1] =im_u[j]
        imagearray[i][j][2]=im_v[j]
rgb=YUV2RGB(imagearray)

filename ="random.png"
matplotlib.image.imsave(filename,rgb.astype(np.uint8))

r=[i for i in range(30,230)for j in range(2)]
g=[i for i in range(30,230)for j in range(2)]
b=[i for i in range(20,220)for j in range(2)]
random.shuffle(r)
random.shuffle(g)
random.shuffle(b)
framearray = np.zeros((400,400,3))
for i in range(400):
    for j in range(400):
        framearray[i][j][0]=r[j]
        framearray[i][j][1] =g[j]
        framearray[i][j][2]=b[j]
filename="aa.png"
matplotlib.image.imsave(filename,framearray.astype(np.uint8))
for h in range(100):
    for i in range(400):
        for j in range(400):
            framearray[i][j][0]=(framearray[i][j][0]+2)%240+10
            framearray[i][j][1] =(framearray[i][j][1]+2)%240+10
            framearray[i][j][2]=(framearray[i][j][2]+2)%240+10
    name = "framee" + str(h)
    matplotlib.image.imsave(name+".bmp",framearray.astype(np.uint8))
for h in range(100):
    integer1 = random.randrange(20,220)
    r = [(integer1 + i)%240+10 for i in range(30,230,4) for j in range(8)]
    g = [(integer1 + i)%240+10 for i in range(30,230,4) for j in range(8)]
    b= [(integer1 + i)%240+10 for i in range(30,230,4) for j in range(8)]
    for i in range(400):
        for j in range(400):
            framearray[i][j][0]=r[j]
            framearray[i][j][1] =g[j]
            framearray[i][j][2]=b[j]
    name = "frame" + str(h)
    matplotlib.image.imsave(name+".bmp",framearray.astype(np.uint8))
fourcc = cv2.VideoWriter_fourcc("D","I","V","X")
video = cv2.VideoWriter("innerframe.avi",fourcc,30,(400,400),True)

for i in range(400):
    filename="frame"+str(i)+".bmp"
    img = cv2.imread(filename)
    video.write(img)
fourcc = cv2.VideoWriter_fourcc("D","I","V","X")
video = cv2.VideoWriter("interframe.avi",fourcc,30,(400,400),True)
for i in range(100):
    filename="framee"+str(i)+".bmp"
    img = cv2.imread(filename)
    video.write(img)
