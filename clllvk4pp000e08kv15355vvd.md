---
title: "Data Migration SQL to No-SQL in AWS"
datePublished: Tue Aug 22 2023 05:37:52 GMT+0000 (Coordinated Universal Time)
cuid: clllvk4pp000e08kv15355vvd
slug: data-migration-sql-to-no-sql-in-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692681152974/ba1f4255-6d04-4492-a7ae-9e0f9c4b2e9a.png
tags: nosql, sql, s3, datamigration, aws-dms

---

Learn how to use AWS DMS service to migrate data

1\. Create DMS data sources & targets (Aurora myQSL RDS, S3 & DynamoDB) 3. Perform data migration including CDC (change data capture)

2\. Create DMS replication instance, endpoints & tasks

3\. Perform data migration including CDC(change data capture)

Prerequisites: Basic understanding of AWS DMS service

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692675767605/6e575ea4-4ffb-441a-9de3-dee48812fa01.png align="center")

**DMS Architecture**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692675946102/4c1ac26a-935e-4cca-a490-691a82a06aed.png align="center")

**Create replication instance in AWS console**

* **First create AWS management console.**
    
* **Go to the AWS\_DMS service and open the AWS DMS service.**
    

![](https://lh4.googleusercontent.com/nNyawmxQlleDHYn-Wjj2mS21gqJNi-IYqQ7Y5Sf2moU9bAeCl0AIqXJpfLgrqVOJ4n6xTCwuoQD3nUZRF8lm2yR73NxgySiDK-sco_u3Fg_9RAwLfxKNgeH5RB_pbCpYAcBCz72k0l-7Pd1BDQzRwQ align="left")

* **And create Replication instance in AWS\_DMS console.**
    

**Create Replication:**

* **Name: “Give a name”**
    
* **Instance class: dms.t3.micro (you can use any class according to your requirement) but here I choose this for practice.**
    
* **Engine version: latest**
    
* **Allocated storage: default**
    
* **Vpc: default**
    
* **Multi Az: According to your requirement (single/multi Az)**
    
* **Public facing ( if you want to disable this public or otherwise leave it ).**
    
* **Advance security & network configuration &gt; replication subnet: default, &gt; vpc security : default.**
    
* **Everything leave as default and click create replication.**
    

**Create AWS RDS in aws console**

![](https://lh5.googleusercontent.com/4VVjqgLCD7U-1wpNRKgIEo5j54GjR6maPTblIkqgvMcXxFZjgOW07vC-RbUq93hVk0fyo1i5ItUkZbZ5WO-g4zs72PbKg-55-_DGu_vU5aPdf4O_lYX4roOYTaWYDwqyfumxpfqjJmbNeJtRsQHS5g align="left")

* Here you select Amazon Aurora Database
    

Follow  below steps.

* Select standard
    
* Select Amazon Aurora
    
* Edition: you will select what you select mysql/postgesql.
    
* Select Amazon Aurora version - default
    
* Select dev/test.
    
* Db instance identifier &gt; “give name”
    
* Master username &gt; admin
    
* Password &gt; 12345678
    
* Db class &gt; db.t3.small
    
* Storage &gt; gp2, Allocated Storage &gt;20, Storage autoscaling &gt; enable, max storage &gt; 10000
    
* Connectivity &gt; Don’t connect to ec2 , Network type &gt; Ipv4
    
* Vpc - default
    
* Db subnet group &gt; default
    
* Public acces &gt; no
    
* Vpc security group &gt; default
    
* And click on create db, wait for 5mins for availability of db.
    

![](https://lh6.googleusercontent.com/2bnfxjSqVNO1Z51_uDkknM4MePQ7PvTRDXyt3C--keWXiUcsBDUEW-jlMRspx4dnlOrBBb_TYGaYH6LGzU44GqzQQ18TsGSyxkDB6ztQxiNcCxJrcSWnCOqsXPoj_e-suQgWdJ58UNn0W17PmsXmQQ align="left")

* **See here we created DB cluster and DB instance.**
    

![](https://lh3.googleusercontent.com/5n0SCSpDitGNZMIMrKBTN2OkCwVdvx7M8f0PZ5L_RjxdUaUskIZPBMLYyyACEe-WCosXbo8ooK2iTvvcUeC4N7fyeZsmudZIwd0hT2Kupt9b7vQch_nA6hnd_XovdNSWC-NS_qvsjJhYbe_JGWJq0w align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692681876626/19c3284f-ff72-4bb0-8e33-5b07e0486f4d.jpeg align="center")

**Create & Configure s3 DMS target**

* Create s3 bucket.
    
* Create IAM Role & Policy for DMS to access s3.
    
* Create DMS s3 Target endpoint & Test.
    
* Here I created bucket name as a “ashok-8000”. You should copy and paste it in note it is used for while creating IAM role.
    

![](https://lh5.googleusercontent.com/XknjphbQuj4jCQ1xKMEWkvPip79mNTvoiBXx12PyNO2Nj5eqTGkee_ZgM0BGN3hqgJLqHVjhIZaMSIwUhG3Gs22lNhbbTeD0BXV5jl3tdJZxCnywtQKXFYEHFiOZkexZwUUYNXBQezOGqdz27wm21Q align="left")

* Now go to IAM management console.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692681937467/8ef0697a-8443-4f07-9e5d-225748cb3ff1.jpeg align="center")

* Here you have created one role for s3 to access DMS service.
    
* And you click on create policy.
    
    ```json
    {
        "Version": "2012-10-17",
        "Statement": [
           {
                "Effect": "Allow",
                "Action": [
                    "s3:PutObject",
    
                    "s3:DeleteObject",
    
                    "s3:PutObjectTagging"
                ],
                "Resource": [
                    "arn:aws:s3:::ashok-8000/*"
                ]
            },
            {
                "Effect": "Allow",
                "Action": [
                    "s3:ListBucket"
                ],
                "Resource": [
                    "arn:aws:s3:::ashok-8000"
                ]
            }
        ]
    }
    ```
    
* Use above DMS\_s3\_acess policy and paste in json box. Create the policy in the name DMS\_S3\_ACCESS.
    
* With help of this policy create one role i.e. DMS\_S3\_ROLE.
    

![](https://lh6.googleusercontent.com/zMn-P3qDZaw0DSR05meVCAJjurwk9QEwqoBtc_D9ckkxVKXDwcw_PXCRl6anzCXnGZGPQ2cpiuLGHit1BZxeMuIkPL7KCYymvBahGmnAF9bDw5ujS3zlXuNoWjP_ya7e_0JNKrHmo2F9NtH187ktAg align="left")

* Now IAM role and policy created. After click on role you should copy the **role arn:** **arn:aws:iam::170161646353:role/DMS\_S3\_ACEESS\_ROLE**
    
* Now you create DMS replication Endpoint for s3 target.
    

![](https://lh3.googleusercontent.com/mO6oDTh4RJcMQH-j7lXa2xGUDigfIjpu2LXQ1RvsU4e7rT49IC7mCbZSq-Kq-Dl6Fzfu0u_Grj63HnhhMsChD4k1_tWZgpVJ1fchlC6WRD4zvDqRwEhOnvAxYzDCsAp49Q0h769uKWu_MLxpXIn9jw align="left")

* Open endpoint console in DMS replication for crating target endpoint s3
    
* ENDPOINTS: Target
    
* Endpoint configuration:
    
* “give a endpoint name”
    
* Target engine: awss3
    
* Service arn role: **arn:aws:iam::170161646353:role/DMS\_S3\_ACEESS\_ROLE**
    
* Bucket name: ashok-8000
    
* Bucket folder: give new folder name
    
* And click on run button you will wait upto status will be successfully.
    

![](https://lh4.googleusercontent.com/-vjXpNjLVia_zSBz6xzfJerSvofjX9WKdmVjR556MBdmsIXBqNXYd9_muqk9stE7SMCsDVTlkaP8rHSTd09jlfOi1-c_Y0zpSeSPbZugeFqDGk3kQGwDBEbiYysP5-VV2LKLyUcc1PC4bJycUs100Q align="left")

* See now we are created the two endpoints in DMS&gt;Endpoint of both s3(target) and mysql(source).
    
* Now we have to Amazon DynamoDB. Before that we have to create IAM role for DynamoDB access like s3.
    

![](https://lh5.googleusercontent.com/g1ZBMdoDTQKDkEaSbUWOVgVInkMdSlZ1XfOGFC559WUbJ3EA1Es1CCyvJqYWVUmAcSmrGPgNJ2KTA0aMRPGfgKkyg-0fNkMAU-97BB3YxEe4LBCgnxQ45NSlza_y8Sj-vKxa5Fssv_-r5hhQFsGlfg align="left")

* Create a role as **DMS\_DynomoDB\_Acess** and give new policies as;
    

```json
{
    "Version": "2012-10-17",
    "Statement": [
    {
        "Effect": "Allow",
        "Action": [
        "dynamodb:PutItem",
        "dynamodb:CreateTable",
        "dynamodb:DescribeTable",
        "dynamodb:DeleteTable",
        "dynamodb:DeleteItem",
        "dynamodb:UpdateItem"
    ],
    "Resource": [
    "arn:aws:dynamodb:us-east-2:170161646353:table/Employee",
    "arn:aws:dynamodb:us-east-2:170161646353:table/awsdms_apply_exceptions",
    "arn:aws:dynamodb:us-east-2:170161646353:table/awsdms_full_load_exceptions"
    ]
    },
    {
        "Effect": "Allow",
        "Action": [
        "dynamodb:ListTables"
        ],
        "Resource": "*"
    }
    ]
}
```

[https://docs.aws.amazon.com/dms/latest/userguide/CHAP\_Target.DynamoDB.html](https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Target.DynamoDB.html)

* Refer this above link for DynamoDB iam role as target access.
    

![](https://lh6.googleusercontent.com/nmdU6STAkKlAA0EWdsi71Dxg8_Hzbp_UCt7hYn4M1KBO239wVT5V1P7yYeSl8oysAl5-zlw6C-veCZCiTygrD4-XI0R2IOZZUCGvWp4uiJsbWaUAJem8iDSesZm4fpwS8qF620Rm_vWQBEgFfT4bkw align="left")

* See above I created DynamoDB new custom role for access DynamoDB as target endpoint from mysql.
    
* Now again go back to the DMS endpoint section and create the one target endpoint for DynamoDB.
    
* Copy the ARN of IAM role and paste at DynamoDB target point. **arn:aws:iam::170161646353:role/DMS\_DynomoDB\_Acess\_role**
    

![](https://lh5.googleusercontent.com/X0xpwcHhGpyNZqcZco4p7eKcAZXSmYlXxDENR1zFNp4hCMWiFCjPGiLQHej-CMrrORdq4nPGnER-Hi13RpV_OPcIrH4m38dAfAZI9K5CO4bul4Krk-N3sZG16lRmyJ1FCu7MnshU0gBfQZia5tfrmQ align="left")

![](https://lh5.googleusercontent.com/IB5rm8wjUdOODgUzQrOH0wI-2GrDRG_EKmqreE3jrz5H11L8AZLfAtuRObn-cfFGcpuNY-Mu6RxhFNlMNBEvxB6LGcE2cBxIux4BDKbBBsGod7xuYfj_THpxOaNfoDQYWZSTjqTArRpSuTbeXVh4uA align="left")

* See in above the screenshot I created three endpoint like 2 target endpoint( DynamoDB & S3) and 1 source enpoint(mysql).
    
* **Now main task will perform like DMS Migration from source to end.**
    
* Before that I must give connection MySQL(source) to server like EC2 of Bastion-host and give **security group of my ip address.** for creating databases, tables, and content. With the help of this content, I have migrated data from source to target .
    
* Open Ec2 and launch instance ( **give sg of my ip address and after launching instances create one more sg as BASTION HOST SG and give port number** **3306 and give the destination ip as private ec2 instance**). connect the MySQL server in instance.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692682061905/8854a855-1393-406e-8289-5d7ae454b54d.jpeg align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692682113896/5c41f9f9-4dff-48ad-93c2-9b945976ce6e.jpeg align="center")

* Now newly created the SG attached to the RDS of source MySQL.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692682171070/de3e13db-0f6c-4eda-93a1-31dcfbfc4548.jpeg align="center")

* After modified , now you have to create the parameter groups in RDS for **Enable binlogs**
    

![](https://lh3.googleusercontent.com/3F-KMBpwARptlh-1O82dMI-NMFwEJTw7ds3lvHLUO_pQbJhuMyd5XahD2rRbwXnzIlNyQ7AcgIANdorQcyu7stfCK6XQP6wG0mmelGYf8DNKkix96AJv848rkKHqBplaUGxvXIY1Cic6SDj__V1C-Q align="left")

* After created this **myrds-cluster-parameter-binlogs,** Open the parameter of what I was created and click on edit parameters and now you have edit the **binlog-checksum**(none) **& binlog-format**(row).
    

![](https://lh5.googleusercontent.com/EUY4s9RDsP-kTCjoOtrnbK4obrIuDFBGhOchvfYzqU7dBu7KKz-v-mpH5BzGwOjJ3K-fIOKVolbO0KFx0RQ7exwPPzPBgx46UCqIwPffU5cXY2_Ym-o9CehHmzKIC55pgWnZYW753yIa_mzjo8ewnA align="left")

* Now this **myrds-cluster-parameter-binlogs attached to RDS of mysql.**
    

![](https://lh3.googleusercontent.com/Og7qnkp3qKHEHqv-wBfL68KZed9N-F0j-eZh3zP7TYWXaSkHFdl9_B4e4NC4G0grx7kvlZpE1E3nq3X5IfzvbiH70hCnWLMCRvEcBqfVaN92fZshABr4Dp4pdZo7R5lk7Mayc2C__iFcuAC-2-BR0w align="left")

* Now download the one sql client in your windows laptop. This is the download link [https://github.com/sqlectron/sqlectron-gui/releases/tag/v1.38.0](https://github.com/sqlectron/sqlectron-gui/releases/tag/v1.38.0) .
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692682250017/afd9a4ce-6b99-4400-8c65-0d87049afd3b.jpeg align="center")

* This is the interface you have downloaded sql eletron client application. And after downloaded you have to give the connection rds to this sql client by click add.
    
* After click add you have give following details:
    

Give name of client, RDS endpoint in HOST, Port number 3306, user & passwd what your given while creating rds. Enable ssh and give ec2 user name and upload key pair pem file of Bastion host of ec2.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692682300546/b8e92ab7-75b9-4d62-a44b-5dfafe09dcd2.jpeg align="center")

* Now click on save and then click connect the rds.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692682393835/054f9468-6d00-44a2-9b51-cf53650f3335.jpeg align="center")

* After click on connect you will get one interface like this
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692682426883/4462a02a-cc5d-4b9a-820f-ef0479145016.jpeg align="center")

* You want to know how many databases are type command SHOW SCHEMAS OR SHOW DATABASES;
    
* And you should give the retention period of your Rds by using following commands.
    

call mysql.rds\_set\_configuration('binlog retention hours', 24);

SHOW VARIABLES LIKE 'log\_bin';

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692682509178/bda64b22-fdb4-457c-9d90-96e5bb632ffe.jpeg align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692682547418/a24128af-7b88-4bfd-a1a1-e3e90fcfc4a5.jpeg align="center")

* Now our retention we were set up to 24 hrs by using above command.
    
* Now **create a database or schema ( create database &lt;name&gt; or create schema &lt;name&gt;).**
    
* **Then use that db or scheme bye using command USE &lt;db name&gt;**
    
* Now create a table in that “mydb” use mydb and then create table following command:
    

```sql
create table if not exists employee (
    empId int auto_increment primary key,
    empName varchar(100)
);
insert into employee value(1, 'emp-1');
insert into employee value(2, 'emp-2');
insert into employee value(3, 'emp-3');
insert into employee value(4, 'emp-4');
```

select \* from employee;

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692681510641/0549e10c-995c-44f5-8f88-d40b975d7364.jpeg align="center")

* Now table is created in ‘mydb’  database.
    
* Now we have to create database 2 tasks\*\*(s3 and Dynamodb)\*\* in DMS console
    

![](https://lh5.googleusercontent.com/cPP7PmYeef0ESUsooqf5wn_Hu_TsBdE5rrUFFHG5JWcuzShniA_P3_FABBRsGd2gBVX1nsrFX-DD9T6irLTLBbqeKKCm5Sd0ZjZpiku34YWQ02okYW3_-iQNtHoPBT0w-RztjgHPLRq0jR5pB7qU2g align="left")

* Now we have create task **‘mysql-s3-task’ and mysql-Dynamodb-task’**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692681626345/45e79a45-d266-4209-9c6a-f7ea28d6d95f.jpeg align="center")

* Now give the source and target resource. And give schema name and table name by clicking add new and remaining leave it as default.
    
* **In migration type you should select only Migrate existing data and replicate ongoing changes.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692681692190/fe42e791-1c2d-4b8d-967b-cbac3b101c31.jpeg align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692681732983/9174ca37-653e-478a-8ef5-2c108bc094b0.jpeg align="center")

* Click on create task
    

![](https://lh4.googleusercontent.com/QPZsLHBS0RcimuG0Ld5mb4L1MTHQMB1AZGyJm5RTUsBvL83cOwVy9XcNoG7HeR6oy3hyBbndNhTpBPrQWWlPwZozxL9EwLDF5Rtum-_xGKZe9xV5ESgAsk25PsnBXWmL8YZdFMgJBpNqeTnwym0bVQ align="left")

* Like you have to create 2 tasks
    
* Now you check the s3 bucket that we give access to DMS
    

![](https://lh4.googleusercontent.com/ql7PXvnG1DzqnaBMbuAB_LIfZyGVU5j9w2XK4FN633JzGDATSyChXNFgjJfQtbkvpzFNBVcHPigaXcCRVotFqGVJC6wNdQgewJNillaLmAarsRrwkq1xO238AGOzZG-hBBguANfTQKMoeUo2-PnV7A align="left")

* Now check **DynamoDB** also
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692677360939/1aae970f-df1c-4f35-8a9b-380f77968060.jpeg align="center")
    

**Finally we did this task as moving content from amazon aurora to s3 & Dynamodb with the help of bastion host.**

Hope you like my blog...!

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692351695778/c9653064-2cfb-48eb-9cf3-9fcc3a16bfe7.png align="center")

If you like the content follow me on LinkedIn: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)

Follow my Whatsapp & telegram community: [https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3](https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3)

[https://t.me/ExplorewithAshok](https://t.me/ExplorewithAshok)

Happy learning......!