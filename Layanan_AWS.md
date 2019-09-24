<h2>AWS Cloud Computing Service</h2>

<p align="center">
  <img src="https://github.com/azispc/AWS/blob/master/result/revolusicloud.png">
</p>
**AWS Cloud Computing**

1. *Amazon Elastis Compute Cloud (EC2)* layanan cloud computing untuk yang berbasis web.[AWS EC2](https://aws.amazon.com/id/ec2/).
2. *Amazon Elastic Map Reduce(EMR)* platform data besar cloud-native yang meproses data dalam jumlah besar dengan cepat. [AWS EMR](https://aws.amazon.com/id/emr/).
3. *Elastic Load Balancing* mendistribusikan lalu lintas aplikasi yang masuk dibeberapa target seperti AWS EC2.


**Layanan Penyimpanan**

1. *Amazon Simple Storage Service (S3)* [AWS S3](https://aws.amazon.com/id/s3/)
2. *Amazon Elastic Block Store (EBS)* merupakan tempat penyimpanan di sistem operasi Amazon EC2.
3. *AWS storage Gateway* layanan penyimpanan cloud hybrid yang memberi akses ke lokasi ke penyimpanan cloud tanpa batas secara virtual.
4. *Amazon CloudFront* layanan jaringan pengantar konten (CDN). Content Delivery Network (CDN) salah satu kegunaannya adalah untuk mempercepat loading website.

**Layanan Database**

1. [*Amazon Relational Database Service (RDS)*](https://aws.amazon.com/id/rds/).
2. [*Amazon DynamoDB*](https://aws.amazon.com/id/dynamodb/) layanan server database yang NoSQL.
3. [*Amazon SimpleDB*](https://aws.amazon.com/id/dynamodb/) sama seperti database DynamoDB namun skalanya lebih kecil.
4. [*Amazon ElastiCache*](https://aws.amazon.com/id/elasticache/).

**Layanan Jaringan**

1. *Amazon Route 53* layann untuk (DNS)
2. *Amazon Virtual Private Cloud (VPC)* membuat private cloud dengan menggabungkan layanan-layanan yang ada dalam Amazon Web Services.

**Layanan Aplikasi**

1. *Amazon CloudSearch* menggabungkan fungsi pencarian yang terdapat pada Amazon Cloud Search.
2. *Amazon Simple Workflow Service (SWF)* mengelola infrastruktur cloud didalam AWS.
3. *Amazon Simple Queue Service (SQS)* layanan sistem antrian satu aplikasi ke aplikasi lainnya.
4. *Amazon Simple Notification Service (SNS)* menyerupai mailing list.
5. *Amazon Simple Email Service (SES)* layanan email server.

**Arsitektur Aplikasi monoLithic VS microService**

<p align="center">
  <img src="https://github.com/azispc/AWS/blob/master/result/monolitikvsmicroservice.png">
</p>

1. *MonoLithic Arsitecture* terdiri **semua** dalam **satu** bagian.

 * Low Cost, Scalable, secure dan reliable.
 * Satu Server handle semua layananan.
 * Maintainace lebih mudah.
 * Deployment yang kompleks.
 * Satu entity pada database berubah maka setiap entity yg sama di database service harus di berubah.

 2. *microService* membagi layanan-layanan yang ada menjadi lebih kecil.
 * HightCost.
 * Setiap layanan memiliki infrastruktur yg berbeda.
 * Proses update aplikasi hanya melingkupi layanan yang terkait.
 * Integrasi komunikasi antar Module mengalami kegagalan.

<p align="center">
  <img src="https://github.com/azispc/AWS/blob/master/result/arsitekturmonovsmicro.png">
</p>
