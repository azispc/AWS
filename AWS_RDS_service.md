**Konfigurasi AWS RDS service By. Console**

**Arsitektur AWS RDS**

<p align="center">
  <img src="https://github.com/azispc/AWS/blob/master/result/arsitektur_rds.png">
</p>

** Membuat VPC dengan private dan public subnet**
1. Buka [AWS Console]() dan **Find Service VPC**.
2. Launch VPC Wizard.
3. Select a VPC Configure
4. Pilih bagian **VPC with Public and Private Subnets** dan isi field berikut :
```
IPv4 CIDR block: 10.0.0.0/16
IPv6 CIDR block: No IPv6 CIDR Block
VPC name: web_server
Public subnet's IPv4 CIDR: 10.0.0.0/24
Availability Zone: us-east-1
Public subnet name: sub_web_pub
Private subnet's IPv4 CIDR: 10.0.1.0/24
Availability Zone: us-west-2a
Private subnet name: sub_web_pri1
Instance type: t2.small
Key pair name: No key pair
Service endpoints: Skip this field.
Enable DNS hostnames: Yes
Hardware tenancy: Default
```
5. Create VPC.
6. Membuat subnet private tambahan pada navigasi dashboard VPC pilih **subnet -> create subnet**
```
Name tag=sub_web_pri2
VPC: pilih vpc yg sudah dibuat sebelumnya*
Avaible Zone: us-east-1b
IPv4 CIDR Block: 10.0.2.0/24
```
7. Create.
<p align="center">
  <img src="https://github.com/azispc/AWS/blob/master/result/rds_2.png">
</p>

8. Membuat security group untuk web server public dan rds DB instance
* security group web server
```
Security group name: sg_webserver
Description: sg web_server
VPC: pilih vpc yg telah dibuat sebelumnya
```
* create and close.
* Security group untuk RDS
```
Security group name: sg_db_webserver
Description: sg web_db_server
VPC: pilih vpc yg telah dibuat sebelumnya
```
* create and close.

<p align="center">
  <img src="https://github.com/azispc/AWS/blob/master/result/rds_3.png">
</p>

9. Pada security group edit inbound rule
* sg_webserver
```
Type: SSH, HTTP
Port: 22, 80
Source: MyIP, AnyWare
```
* sg_db_webserver
```
Type: mysql
port: 3306
Source: AnyWare
```

**Konfigurasi DB Subnet Groups**
1. Buka **AWS Console** Find Service **RDS**
2. Pada navigasi **rds** pilih **Subnet Groups**
```
Name: web_db_group
Description: DB Subnet Group
VPC: pilih VPC yang sudah dibuat
```
3. Add Subnets dan pilih **Add all the subnets related to this VPC**
4. Create dan Selesai.
<p align="center">
  <img src="https://github.com/azispc/AWS/blob/master/result/rds_4.png">
</p>

**Membuat dan Konfigurasi RDS by.Console**
1. Buka **AWS Console** Find Service **RDS**
2. Pada navigasi **rds** pilih **Database**
3. Create **Database**
4. Select Engine  **MySQL** dan Next
5. **Choose use Case** pilih **Dev/Test-MySql**
6. Specify DB detail
```
License model: Use the default value.
DB engine version: Use the default value.
DB instance class: db.t2.small
Multi-AZ deployment: No
Storage type: General Purpose (SSD)
Allocated storage: 20 GiB
DB instance identifier: web_db_server
Master username: web_server
Master password: Choose a password.
Confirm password: Retype the password
```
7. Next
8. Configure Advanced Setting
```
VPC: pilih vpc yg sebelumnya di buat (Zone harus berbeda)
Subnet Group: web_db_group
Public accessibility: No
Availability zone: No Preference
VPC security groups: sg_db_webserver (sudah dibuat sebelumnya)
Database name: samplepage
```
9. Create Database
10. View DB instances details dan tunggu sampai available pada DB status
11. Selesai catat endpoint dan port dari databasenya.

<p align="center">
  <img src="https://github.com/azispc/AWS/blob/master/result/rds_5.png">
</p>


**Membuat EC2 Instance by.console**
1. buka AWS console untuk EC2 **Find Service**
2. Launch Instance
3. Choose as Instance Type

```
Family: General purpose
Type: t2 small
vCPUs: 1
Memory:2 GiB
Instance Storage: EBS only
Network Performance: Low to Moderate
IPv6 Support: Yes
```

4. Next: **Configure Instance Details**

```
Purchasing option : -
Network: pilih VPC yang sudah dibuat
Subnet: susiai subnet yg dibuat VPC.
Auto assign Public group: Enable
Capasity Reservation: Open
IAM role: None
Shutdown behavior: Stop
```

5. Next: Add Storage

```
Volume type: Root
Device: /dev/xvda
Snapshot: snap-05a1---
Size: 8 GiB
Volume Type: SSD
IOPS: 100/3000
Throughput: N/A (MB/s)
Delete on termination: ok
Encryption: Not-Encryption
```

6. Next: Add Tags

```
Key: name
Value: web_server
Instance: ok
Volume: ok
```

7. Next: Configure Security group pilih **Select an existing security Group**

```
Security Group ID: SG yg telah dibuat pd VPC
Name:
Description:
Actions:
```

8. Review and Launch

9. Select an existing key pair or create a new key pair

```
Create a new key pair
Key pair name: MyKeyPair
```
10. Launch And selesai.

<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/rds_6.png">


**Instal Apache Web Server dan PHP**
1. Remote EC2 instance sebelunya dibuat menggunakan SSH
2. Berhasil remote silhakan lakukan update
```
$ sudo yum update -y
```
3. Install https, PHP dan mySQL
```
$ sudo yum install -y httpd24 php56 php56-mysqlnd
```
4. Menjalankan web server Apache
```
$ sudo service httpd start
$ sudo chkconfig httpd on (supaya selalu on ketika booting)
```
5. Set Apache
```
$ sudo groupadd www (set permission pada apache dan menambahkan group dgn nama www)
$ sudo usermod -a -G www ec2-user (menambahkan ec2-user kepada group ke www)
$ exit (login lagi pakai SSH)
$ groups (ec2-user wheel www)
$ sudo chown -R root:www /var/www (mengubah ownwership pada www)
$ sudo chmod 2775 /var/www (menambahkan permissin write)
```

6. Menghubungkan Apache dengan db instace
```
$ mkdir inc /var/www/
$ cd ~/var/www/inc/
$ sudo tee /var/www/inc/dbinfo.inc << EOF
<?php
define('DB_SERVER', 'DB_instance_enpoind');
define('DB_USERNAME', 'DB_USERNAME');
define('DB_PASSWORD', 'DB_PASSWORNYA');
define('DB_DATABASE', 'sample');
?>
EOF
```
7.  Membuat file html di direktori /var/html/ dengan nama file [samplepage.php](https://github.com/azispc/AWS/blob/master/page/samplepage.html)

```
$ wget "https://github.com/azispc/AWS/blob/master/page/samplepage.html"
$ sudo mv samplepage.html ~/var/www/html/
```
8. Selesai dan silahkan access melalui IP Public seperti berikut ini.

<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/rds_7.png">
