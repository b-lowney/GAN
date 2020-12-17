# GAN

Authors: Brydon Lowney, Ivan Lokmer, Gareth O'Brien, Chris Bean

Contact email: brydon.lowney@ucdconnect.ie 

Data and Trained Models can be found at https://drive.google.com/drive/folders/1b5XAbJgGbWuJ9wJo61tvLAR__NFPIUMY?usp=sharing

This repository contains the code for training and predicting a GAN on seismic data, originally for the purpose of diffraction separation. 
The trained model for diffraction separation can be found at the above link alongside some open-source data courtesy of the USGS (https://walrus.wr.usgs.gov/namss/survey/p1-13-la-walker-ridge/) which can be used to test the code.
Alongside this, PWD data of the same seismic dataset is provided which can be used for comparison and was generated using the following code:


bash$ sfsegyread tfile=WR_tfile.rsf hfile=WR_hfile.ebcdic bfile=WR_bfile.bin endian=y verb=y < WR332a-stack.sgy > WR.rsf

bash$ sfdip < WR.rsf > WR_DIP.rsf rect1=10 rect2=10 order=5 verb=y

bash$ sfpwspray < WR.rsf dip=WR_DIP.rsf > WR_SPRAY.rsf ns=2

bash$ sfstack < WR_SPRAY.rsf > WR_STACK.rsf axis=2

bash$ sfadd < WR.rsf WR_STACK.rsf scale=1,-1 > WR_PWD.rsf 

bash$ sfsegywrite < WR_PWD.rsf > WR332a-PWD.sgy tfile=WR_tfile.rsf hfile=WR_hfile.ebcdic bfile=WR_bfile.bin endian=0 verb=y


GAN code was written using templates on https://machinelearningmastery.com/how-to-develop-a-pix2pix-gan-for-image-to-image-translation/ 

Original uploaded 08/09/2020
