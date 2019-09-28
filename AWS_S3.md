**AWS S3**

1. Buka [AWS Console]() Management Service
2. Find Service **S3** maka akan masuk ke halaman [Amazon S3]()
3. Create Bucket
```
Bucket Name: masbocket
Region: us-east-1
Copy setting from an existing bucket:
```
<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/s3_1.png">
</p>

4. create.

<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/s3_2.png">
</p>

5. Buka **masbocket** dan Create Folder
```
Name folder: news
Encryption: None (Use bucket settings)
```
6. Kembali ke bocket **masbocket** untuk menjadikan foldernya menjadi public.

<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/s3_5.png">
</p>

7. Pilih Upload File pada **masbocket/news/**
<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/s3_3.png">
</p>

<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/s3_4.png">
</p>
8. Next.
9. klik **file** dengan nama **helloworld.html** dan pilih *Make public* supaya dapat diakses oleh komputer lain dengan link berikut ini:
```
https://masbocket.s3.amazonaws.com/news/helloworld.html
```
<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/hello_1.png">
</p>

10.Selesai.
<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/hello_2.png">
</p>



**Memindahkan File antar bucket berbeda**

<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/hello_6.png">
</p>

1. Buka AWS Console
2. Find Service S3
3. Buka bucket dengan nama **masbocket** dan buka folder **news**
4. Klik file dengan nama **helloworld** pilih action **copy**

<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/hello_3.png">
</p>

5. Lalu buka bucket **masbocket1** dan buka foder **second**
6. Pilih **Action** dan pilih **Paste**

<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/s3_5.png">
</p>
