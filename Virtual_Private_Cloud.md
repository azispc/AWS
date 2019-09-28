<h2>AWS Virtual Private CLoud (VPC)</h2>

Note: Your Instances will launch in the US East (N. Virginia)

**AWS Virtual Private Cloud (VPC) Step by Step**

1. sudah memiliki akun AWS
2. buka [vpc console](https://console.aws.amazon.com/vpc/) atau melalui AWS Console pada vocareum dan akan terbukan halaman manajemen console AWS seperti gambar dibawah ini
3. pastikan region sama saat selama menjalankan AWS
4. pilih **AWS Service** pada **Find Service** ketik VPC dan pilih
5. pada **VPC Dashboard** silahkan klik Launch **VPC Wizard**
<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_1.png">
</p>

6. select VPC configure
<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_2.png">
</p>
7. VPC with a singgle Public subnet

```
IP4 CIDR block:10.0.0.0/16
IPV6 CIDR: No.IPV6 CIDR block
VPC name : vpc_maz
Public subnet IPV4 CIDR: 10.0.0.0/24
Available Zone: No Preference
Subnet name: sub_maz
Service Endpoint
Enable DNS hostname: Yes
Hardware tenancy: Default
```

<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_3.png">
</p>

8. **Create** VPC and **Ok**

<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_4.png">
</p>

**Security Group**
1. pada navigasi Dashboard pada VPN pada bagian **Security**

<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_5.png">
</p>
2. Create security group

```
Security group name: myserver_maz
Description: myserver by asw
VPC: pilih VPC yang dibuat
```
<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_6.png">
</p>
3. create
4. membuat rule protokol **Inbound Rules** Edit Rules

```
Type: SSH
Protocol: TCP
Port range: 22
Source: anyware
Description: ---
```

<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_7.png">
</p>

<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_8.png">
</p>

5. Save rules
6. Close.
<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_9.png">
</p>

**AWS EC2 type Instance t2 micro**
1. buka AWS console untuk EC2 **Find Service**
2. Launch Instance

<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_10.png">
</p>

3. Choose as Instance Type

```
Family: General purpose
Type: t2 micro
vCPUs: 1
Memory:1 GiB
Instance Storage: EBS only
Network Performance: Low to Moderate
IPv6 Support: Yes
```

<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_11.png">
</p>

4. Next: **Configure Instance Details**

```
Purchasing option : -
Network: pilih VPC yang sudah dibuat
Subnet: susiai subnet yg dibuat VPC.
Auto assign Public group: -
Capasity Reservation: Open
IAM role: None
Shutdown behavior: Stop
```
<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_12.png">
</p>

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
<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_13.png">
</p>

6. Next: Add Tags

```
Key: name
Value: serverlinux_maz
Instance: ok
Volume: ok
```
<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_14.png">
</p>

7. Next: Configure Security group pilih **Select an existing security Group**

```
Security Group ID: SG yg telah dibuat pd VPC
Name:
Description:
Actions:
```
<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_15.png">
</p>

8. Review and Launch

<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_14.png">
</p>
9. Select an existing key pair or create a new key pair

```
Create a new key pair
Key pair name: MyKeyPair
```
10. Launch And selesai.

<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_15.png">

</p>
<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_15a.png">
</p>
<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_15b.png">

</p>
<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_15c.png">

</p>
<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_15d.png">
</p>


**Konfigurasi Elastis IPs melalui navigasi Dashboard VPC**
1. Pada navigasi dashboard pilih **Elastis IPs**

<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_16.png">
</p>

2. Allocate new address

```
Scope: VPC
IPv4 address pool: Amazon pool
```
<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_17.png">
</p>

3. Allocate
4. CLose

<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_18.png">
</p>

5. Associate address

```
Resource type: Instance
Instance: pilih nama instance yg telah dibuat
Private IP: sesuai VPC pada EC2
Reassocian:-
```
<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_19.png">
</p>

6. Selesai.


**Konfigurasi Elastis IPs melalui navigasi Dashboard EC2**
1. Pada Navigasi Dashboard EC2 pilih bagian **Security** pilih **Elastis IPs**
2. Allocate new address
```
Scope: VPC
IPv4 address pool: Amazon pool
```
3. Allocate
4. Close.
5. Pada halaman jendela **Elastis IPs** Pilih IPs yang tadi dibuat. pilih pada menu action **Associate address**
6. **Associate address**
```
Resource type: Instance
Instance: pilih nama instance yg telah dibuat
Private IP: sesuai VPC pada EC2
Reassocian:-
```
7. Associate.

**Remote AWS EC2 menggunakan SSH pada OS ubuntu**

1. Download **KeyPair** pada EC2 pada navigasi dashboard EC2 pilih bagian **KeyPair**
```
Create Key pair: keypair_maz_27.09_2019.pem
```
2. Install SSH pada ubuntu
```
sudo apt install ssh -y
```
4. ganti permission KeyPair dengan **chmod 400**
```
chomd 400 keypair_maz_27_09_2019.pem
```
3. silahkan remote EC2 dengan seperti berikut
```
ssh -i key.pem hostname@IPv4_pubic
ssh -i keypair_maz_27_09_2019.pem ec2-user@IPv4_pubic
```
<p align="center">
<img src="https://github.com/azispc/AWS/blob/master/result/byMaz_20.png">
</p>

**Source**
* [AWS VPC](https://docs.aws.amazon.com/vpc/index.html).
* [AWS EC2](https://docs.aws.amazon.com/ec2/index.html).
