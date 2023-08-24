---
title: "Build 3-tier Architecture of PHP-LAMP with Terraform Tool #part-2"
datePublished: Fri Aug 04 2023 07:09:27 GMT+0000 (Coordinated Universal Time)
cuid: clkw8wktm000j09l34g1z1q89
slug: build-3-tier-architecture-of-php-lamp-with-terraform-tool-part-2
tags: devops, terraform, 90daysofdevops, 3-tier-architecture

---

Hello Friends,

I hope u guys like my 1st part of the 3-tier php-lamp using Terraform. Now here I am going a write 2nd part of the blog.

Let's Start...👍

**Prerequestance of this project**:

1. Vscode.
    
2. Aws management console account.
    
3. IAM user in AWS (that user has AdministratorAcess)
    
4. Generate an Access key and a Secret key for that user.
    
5. install terraform extension on Vscode.
    

**Step-1**

* Login into your Aws account by giving your "user-id" and "password".
    
* Then go to the search box of AWS and search it for IAM(Identity and Access Management).
    

![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj6-gs5AEbI8ntbgEM_nmWT8HiW39OZeQcFYP0kewJzSVd8vOlevvqfT1mzi91GRwEve6LbYYZyK7TxO9hfk9pul8rO88yLEVX7e4bmBQywXEj9fFsxxv4xOM7FlkzYmkMRRScwmJTVjfy1XIhln9ffMEYItpBs7kFege0RfUuv-53yM5GTG67nQnIMVw/w518-h313/blog.png align="left")

  

* Create an IAM user for Access to Terraform inside the AWS cloud.
    

![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg-dMExJnRxLvo1tnbjBeNiuSFdYKN65fGn9iGXZxF2akeOHtXx6jHhfH_3AT6Ujfy26ICdtE8FC86K53p9wkWXJhwz0Rmuj3Cf9JXsGKiR881nmczQCTfmml4vZriGW5vipV6vYKOS23u4a9U4_bWyvEUpFpM1V5T1w-C4-U7C17DWVTs5UEki6JuwgA/w538-h147/Screenshot%202023-06-13%20120131.png align="left")

* Give the AdminstratorAccess to that user.
    

![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgSzKWR9KRZVczbVu2Bh3AnqHdYd979o_Of3CppYmF1Sz-bDtqYSd9lf1MRPtneVJYBQ7WYknO4k3H3XGwZw0FXJZvFOYlXpKxJ9nt9_yVA3_PAmBL4SiHaFSILSpuaDeZPamLn2eu4_XWkJ-0D6RkBdZqHrsiJs7SH4sUh6hgscSGDxigdszPcd46o-Q/w565-h130/Screenshot%202023-06-13%20120457.png align="left")

* Now generate the Access key and Secret Key for that user.
    
* For this go to the user and click on security credentials.
    

![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhqzkLaxhsMsZMo01SqK3xD_Ba3Bam-bYNKNhYizJZ9gQOvF1qsRWx3bLW_Xpa6iPaNIml7oy55K7l-oF8MkaLCFYr8JN1SRlcOoQC48b7yDvJckS_pql6ub9XcaMQVmHtfbyAA8CyoO7sqTpjPyWsCktdVFJLQ7GgMFYfwT5_8JzhAUr8RKbOw4x_pdQ/w585-h250/Screenshot%202023-06-13%20121025.png align="left")

  

* After clicking on Security credentials and scrolling down slowly you will get the "Access-key" option. 
    
* Generate the keys. Select the CLI &gt;&gt; Access key and Secret generated successfully.
    
* Finally, save it in the notepad for further usage.
    

**Step-2**

* Open Vscode and install Terraform extension, Aws cli tool kit
    

![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh8Z7n0Ck-WbbCp9aF3XyGOr4L2DAmFNJu46-bAhQudHUh_d0vJEcJJb9pZIYxTxnhXsp92bakMIGot4GF5BvobB3u8x6TdjkWonpa1cWccNjUTJTepZ-S-B4eJgKvJigPw77P4Pg7xOup5oOzlXsdlejdQk7kAQ3KtQfvvPfCS1FL9fxzF4rdswJN8nQ/w497-h213/Screenshot%202023-06-13%20122018.png align="left")

![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhboO-CS4DtyZUXewBkZ5BztlwtAVgqAURZD0HClO6d_1utf18AFApN6typrMk4zi4nG_etAtYdFEgARE0nQ1oie0hnZbl3k2HLTm8BzKrQlCFGxjlWQbT9gdmz7OdXXSMXL0Anb1fZZOKIDCy8Y4gVcuqoVVkjgEvrSSBJ9lG6pcIkzzqTY3kGdYfesA/w530-h224/Screenshot%202023-06-13%20122122.png align="left")

  

* Now create terraform files for creating infrastructure.
    
* create a file with extension of ".tf".
    

![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi56CW5J3qhlUgHIKYPp_DIK9Sz8bpwHL3fPD3N_CwzbVpNkSCF36UOJejt79e2hhn7_gLpoY0LLnyzxDsC273lQ6UKtcsvFtKVVsyBHejLhVdklS15Av0K1Btfa0GltrBLRZl4a0btyhhr1o2InGzgJZZeOmFTLRcFJltKgin8llutGBNZWjwOZsIvCA/w318-h282/Screenshot%202023-06-13%20123709.png align="left")

  
[**vpc.tf**](http://vpc.tf)

* Here I created 1vpc (php-vpc) &gt; cidr range=10.0.0.0/16
    
* 2 public subnets (public-sub1, public-sub2) &gt; cidr range=10.0.1.0/24, 10.0.2.0/24 &gt; azs = ap-south-1a, ap-south-1b.
    
* 4 private subnets (web-sub1, web-sub2, db-sub1 & db-sub2) &gt; cidr range=10.0.3.0/24, 10.0.4.0/24, 10.0.5.0/24, 10.0.6.0/24 &gt; azs = ap-south-1a, ap-south-1b.
    
* Internet gateway.
    
* NAT gateway for providing internet to private servers.
    
* Elastic Ip for making static IP address to the webservers.
    
* 2 Route tables (Public and private)
    
* route associations.
    
* subnet associations.
    

#create vpc

resource "aws\_vpc" "php-vpc" {

  cidr\_block       = "10.0.0.0/16"

  instance\_tenancy = "default"

  tags = {

    Name = "php-vpc"

  }

}

#creating Public subnets for jump-box server

#Public subnet-1

resource "aws\_subnet" "public-sub1" {

  vpc\_id     = aws\_vpc.php-vpc.id

  cidr\_block = "10.0.1.0/24"

  map\_public\_ip\_on\_launch = true

  availability\_zone = "ap-south-1a"

  tags = {

    Name = "public-sub1"

  }

}

#Public subnet-2

resource "aws\_subnet" "public-sub2" {

  vpc\_id     = aws\_vpc.php-vpc.id

  cidr\_block = "10.0.2.0/24"

  map\_public\_ip\_on\_launch = true

  availability\_zone = "ap-south-1b"

  tags = {

    Name = "public-sub2"

  }

}

#creating Private Subnets

#private subnet1 - Web-app

resource "aws\_subnet" "Web-sub1" {

  vpc\_id     = aws\_vpc.php-vpc.id

  cidr\_block = "10.0.3.0/24"

  availability\_zone = "ap-south-1a"

  tags = {

    Name = "Web-sub1"

  }

}

#private subnet2 - Web-app

resource "aws\_subnet" "Web-sub2" {

  vpc\_id     = aws\_vpc.php-vpc.id

  cidr\_block = "10.0.4.0/24"

  availability\_zone = "ap-south-1b"

  tags = {

    Name = "Web-sub2"

  }

}

#Private subnet1 - Database

resource "aws\_subnet" "db-sub1" {

  vpc\_id     = aws\_vpc.php-vpc.id

  cidr\_block = "10.0.5.0/24"

  availability\_zone = "ap-south-1a"

  tags = {

    Name = "DB-sub1"

  }

}

#private subnet2 - Database

resource "aws\_subnet" "db-sub2" {

  vpc\_id     = aws\_vpc.php-vpc.id

  cidr\_block = "10.0.6.0/24"

  availability\_zone = "ap-south-1b"

  tags = {

    Name = "DB-sub2"

  }

}

\# Creating Internet Gateway 

resource "aws\_internet\_gateway" "php\_igw" {

  vpc\_id = aws\_vpc.php-vpc.id

  tags = {

    Name = "demoigw"

  }

}

\# Create NAT Gateway

resource "aws\_nat\_gateway" "nat\_gateway" {

  allocation\_id = aws\_eip.nat\_eip.id

  subnet\_id     = aws\_subnet.public-sub1.id

  tags = {

    Name = "php-nat"

  }

}

\# Create EIP for NAT Gateway

resource "aws\_eip" "nat\_eip" {

  vpc      = true

  tags = {

    Name = "php-nat-eip"

  }

}

\# Creating Public Route Table

resource "aws\_route\_table" "Public\_rt" {

    vpc\_id = aws\_vpc.php-vpc.id

route {

        cidr\_block = "0.0.0.0/0"

        gateway\_id = aws\_internet\_gateway.php\_igw.id

    }

tags = {

        Name = "Public Rt"

    }

}

\# Creating Private Route Table

resource "aws\_route\_table" "Private\_rt" {

    vpc\_id = aws\_vpc.php-vpc.id

    tags = {

      Name = "Private Rt"

    }

}

\# Associate NAT Gateway with the Private Route Table

resource "aws\_route" "private\_rt\_nat\_gateway" {

  route\_table\_id            = aws\_route\_table.Private\_rt.id

  destination\_cidr\_block    = "0.0.0.0/0"

  nat\_gateway\_id            = aws\_nat\_gateway.nat\_gateway.id

}

\# Associating Route Table to jumpbox sunbets

resource "aws\_route\_table\_association" "public\_rt\_association\_subnet1" {

    subnet\_id = aws\_subnet.public-sub1.id

    route\_table\_id = aws\_route\_table.Public\_rt.id

}

resource "aws\_route\_table\_association" "public\_rt\_association\_subnet2" {

    subnet\_id = aws\_subnet.public-sub2.id

    route\_table\_id = aws\_route\_table.Public\_rt.id

}

\# Associating Route Table to web subnets

resource "aws\_route\_table\_association" "private\_rt\_assocaiation\_subnet3" {

    subnet\_id = aws\_subnet.Web-sub1.id

    route\_table\_id = aws\_route\_table.Private\_rt.id

}

resource "aws\_route\_table\_association" "private\_rt\_assocaiation\_subnet4" {

    subnet\_id = aws\_subnet.Web-sub2.id

    route\_table\_id = aws\_route\_table.Private\_rt.id

}

\# Associating Route Table to db sunbets

resource "aws\_route\_table\_association" "private\_rt\_assocaiation\_subnet5" {

    subnet\_id = aws\_subnet.db-sub1.id

    route\_table\_id = aws\_route\_table.Private\_rt.id

}

resource "aws\_route\_table\_association" "private\_rt\_assocaiation\_subnet6" {

    subnet\_id = aws\_subnet.db-sub2.id

    route\_table\_id = aws\_route\_table.Private\_rt.id

}

  
[**Pubec2.tf**](http://Pubec2.tf)

* In this file I created one jumpbox, 2 web ec2, 2sg (jumpsg & websg).
    
* In user\_data I given commands for installation of php, php-mysql(connection between the PHP & MySQL ), git and httpd.
    
* finally in script I was given the database enpoint, database user, password and identifier.
    

\# Creating 1st EC2 instance in Public Subnet1

resource "aws\_instance" "jumpbox" {

  ami                         = "ami-049a62eb90480f276"

  instance\_type               = "t2.micro"

  count                       = 1

  key\_name                    = "eminds"

  vpc\_security\_group\_ids      = \[aws\_security\_group.jumpsg.id\]

  subnet\_id                   = aws\_subnet.public-sub1.id

  associate\_public\_ip\_address = true

tags = {

    Name = "Jumpbox-Ec2"

  }

}

\# Creating 1st EC2 instance in Public Subnet1

resource "aws\_instance" "Web1" {

  ami                         = "ami-049a62eb90480f276"

  instance\_type               = "t2.micro"

  count                       = 1

  key\_name                    = "eminds"

  vpc\_security\_group\_ids      = \[aws\_security\_group.Websg.id\]

  subnet\_id                   = aws\_subnet.Web-sub1.id

  associate\_public\_ip\_address = false

  user\_data                   = &lt;&lt;-EOT

  #!/bin/bash

    yum update -y

    yum install git -y

    yum install -y httpd wget php-fpm php-mysqli php-json php php-devel

    systemctl start httpd

    systemctl enable httpd

    systemctl status httpd

    usermod -a -G apache ec2-user

    chown -R ec2-user:apache /var/www

    git clone [https://github.com/Akiranred/php-lamp.git](https://github.com/Akiranred/php-lamp.git) /var/www/html

    cd /var/www/html/php

    sudo bash -c 'echo "&lt;?php

    function Createdb(){

      \\$servername = \\"${aws\_db\_instance.rds\_database.endpoint}\\";

      \\$username = \\"admin\\";

      \\$password = \\"12345678\\";

      \\$dbname = \\"bookstore\\";

      // create connection

      \\$con = mysqli\_connect(\\$servername, \\$username, \\$password);

      // Check Connection

      if (!\\$con){

          die(\\"Connection Failed : \\" . mysqli\_connect\_error());

      }

      // create Database

      \\$sql = \\"CREATE DATABASE IF NOT EXISTS \\$dbname\\";

      if(mysqli\_query(\\$con, \\$sql)){

          \\$con = mysqli\_connect(\\$servername, \\$username, \\$password, \\$dbname);

          \\$sql = \\"

                          CREATE TABLE IF NOT EXISTS books(

                              id INT(11) NOT NULL AUTO\_INCREMENT PRIMARY KEY,

                              book\_name VARCHAR (25) NOT NULL,

                              book\_publisher VARCHAR (20),

                              book\_price FLOAT

                          );

         \\";

          if(mysqli\_query(\\$con, \\$sql)){

              return \\$con;

          }else{

              echo \\"Cannot Create table...!\\";

          }

      }else{

          echo \\"Error while creating database \\" . mysqli\_error(\\$con);

      }

    }

    ?&gt;" &gt; /var/www/html/php/db.php'

    systemctl restart httpd

    EOT

tags = {

    Name = "Web-Ec2-1"

  }

}

\# Creating 2nd EC2 instance in Public Subnet2

resource "aws\_instance" "Web2" {

  ami                         = "ami-049a62eb90480f276"

  instance\_type               = "t2.micro"

  count                       = 1

  key\_name                    = "eminds"

  vpc\_security\_group\_ids      = \[aws\_security\_group.Websg.id\]

  subnet\_id                   = aws\_subnet.Web-sub2.id

  associate\_public\_ip\_address = false

  user\_data                   = &lt;&lt;-EOT

  #!/bin/bash

    yum update -y

    yum install git -y

    yum install -y httpd wget php-fpm php-mysqli php-json php php-devel

    systemctl start httpd

    systemctl enable httpd

    systemctl status httpd

    usermod -a -G apache ec2-user

    chown -R ec2-user:apache /var/www

    git clone [https://github.com/Akiranred/php-lamp.git](https://github.com/Akiranred/php-lamp.git) /var/www/html

    cd /var/www/html/php

    sudo bash -c 'echo "&lt;?php

    function Createdb(){

      \\$servername = \\"${aws\_db\_instance.rds\_database.endpoint}\\";

      \\$username = \\"admin\\";

      \\$password = \\"12345678\\";

      \\$dbname = \\"bookstore\\";

      // create connection

      \\$con = mysqli\_connect(\\$servername, \\$username, \\$password);

      // Check Connection

      if (!\\$con){

          die(\\"Connection Failed : \\" . mysqli\_connect\_error());

      }

      // create Database

      \\$sql = \\"CREATE DATABASE IF NOT EXISTS \\$dbname\\";

      if(mysqli\_query(\\$con, \\$sql)){

          \\$con = mysqli\_connect(\\$servername, \\$username, \\$password, \\$dbname);

          \\$sql = \\"

                          CREATE TABLE IF NOT EXISTS books(

                              id INT(11) NOT NULL AUTO\_INCREMENT PRIMARY KEY,

                              book\_name VARCHAR (25) NOT NULL,

                              book\_publisher VARCHAR (20),

                              book\_price FLOAT

                          );

         \\";

          if(mysqli\_query(\\$con, \\$sql)){

              return \\$con;

          }else{

              echo \\"Cannot Create table...!\\";

          }

      }else{

          echo \\"Error while creating database \\" . mysqli\_error(\\$con);

      }

    }

    ?&gt;" &gt; /var/www/html/php/db.php'

    systemctl restart httpd

    EOT

tags = {

    Name = "Web-Ec2-2"

  }

}

\# Creating Security Group 

resource "aws\_security\_group" "jumpsg" {

  vpc\_id = aws\_vpc.php-vpc.id

  #inboud rules for jump box

  # SSH access from anywhere

  ingress {

    from\_port   = 22

    to\_port     = 22

    protocol    = "tcp"

    cidr\_blocks = \["0.0.0.0/0"\]

  }

  # Outbound rules

  egress {

    from\_port   = 0

    to\_port     = 0

    protocol    = "-1"

    cidr\_blocks = \["0.0.0.0/0"\]

  }

}

resource "aws\_security\_group" "Websg" {

  vpc\_id = aws\_vpc.php-vpc.id

  # Inbound Rules

  # HTTP access from anywhere

  ingress {

    from\_port   = 80

    to\_port     = 80

    protocol    = "tcp"

    cidr\_blocks = \["0.0.0.0/0"\] 

  }

    ingress {

    from\_port   = 22

    to\_port     = 22

    protocol    = "tcp"

    cidr\_blocks = \["0.0.0.0/0"\]

  }

\# HTTPS access from anywhere

  ingress {

    from\_port   = 443

    to\_port     = 443

    protocol    = "tcp"

    cidr\_blocks = \["0.0.0.0/0"\]

  }

\# for database server

  ingress {

    from\_port   = 3306

    to\_port     = 3306

    protocol    = "tcp"

    cidr\_blocks = \["0.0.0.0/0"\]

  }

\# Outbound Rules

  # Internet access to anywhere

  egress {

    from\_port   = 0

    to\_port     = 0

    protocol    = "-1"

    cidr\_blocks = \["0.0.0.0/0"\]

  }

tags = {

    Name = "Web-SG"

  }

}

  

[**Pvt.tf**](http://Pvt.tf)

* Here I created 2 db ec2, 1 dbsg.
    
* In user\_data I have given commands for the installation of MariaDB and database endpoint. 
    

\# Creating 1st EC2 instance in Private Subnet1

data "aws\_db\_instance" "rds" {

  db\_instance\_identifier = aws\_db\_instance.rds\_database.identifier

}

resource "aws\_instance" "dbec2-1" {

  ami                         = "ami-049a62eb90480f276"

  instance\_type               = "t2.micro"

  count                       = 1

  key\_name                    = "eminds"

  vpc\_security\_group\_ids      = \[aws\_security\_group.dbsg.id\]

  subnet\_id                   = aws\_subnet.db-sub1.id

  associate\_public\_ip\_address = false

  user\_data                   = &lt;&lt;-EOT

  #!/bin/bash

  yum -y install mariadb105-server

  systemctl start mariadb

  systemctl enable mariadb

  DB\_ENDPOINT="${[data.aws](http://data.aws)\_db\_instance.rds.endpoint}

   EOT

tags = {

    Name = "dbec2-1"

  }

}

\# Creating 2nd EC2 instance in Private Subnet2

resource "aws\_instance" "dbec2-2" {

  ami                         = "ami-049a62eb90480f276"

  instance\_type               = "t2.micro"

  count                       = 1

  key\_name                    = "eminds"

  vpc\_security\_group\_ids      = \[aws\_security\_group.dbsg.id\]

  subnet\_id                   = aws\_subnet.db-sub2.id

  associate\_public\_ip\_address = false

  user\_data                   = &lt;&lt;-EOT

  #!/bin/bash

  yum -y install mariadb105-server

  systemctl start mariadb

  systemctl enable mariadb

  DB\_ENDPOINT="${[data.aws](http://data.aws)\_db\_instance.rds.endpoint}

   EOT

tags = {

    Name = "dbec2-2"

  }

}

\# Creating Security Group 

resource "aws\_security\_group" "dbsg" {

  vpc\_id = aws\_vpc.php-vpc.id

#inbound rules

ingress {

    from\_port   = 22

    to\_port     = 22

    protocol    = "tcp"

    cidr\_blocks = \["0.0.0.0/0"\]

  }

ingress {

    description     = "Allow traffic from application layer"

    from\_port       = 3306

    to\_port         = 3306

    protocol        = "tcp"

    cidr\_blocks     = \["0.0.0.0/0"\]

  }

\# Outbound rules

egress {

    from\_port   = 0

    to\_port     = 0

    protocol    = "-1"

    cidr\_blocks = \["0.0.0.0/0"\]

  }

tags = {

    Name = "DB SG"

  }

}

[**Credentials.tf**](http://Credentials.tf)

provider "aws" {

  region     = "ap-south-1"

  access\_key = "your\_access\_key"

  secret\_key = "&lt;your\_secret key&gt;"

}

[**variables.tf**](http://variables.tf)  

* Here I given the variable for target group arn for connection to load balancer.
    

\# Declare target\_group\_arn variable

variable "target\_group\_arn" {

  type    = string

  default = "aws\_lb\_target\_group.target-group.arn"

}

[**rds.tf**](http://rds.tf)

* Here I created the rds of mariadb version 10.5
    

\# Creating RDS Instance

resource "aws\_db\_subnet\_group" "rds\_database" {

  name       = "main"

  subnet\_ids = \[aws\_subnet.db-sub1.id, aws\_subnet.db-sub2.id\]

tags = {

    Name = "My DB subnet group"

  }

}

resource "aws\_db\_instance" "rds\_database" {

  engine            = "mariadb"

  engine\_version    = "10.5.16"

  instance\_class    = "db.t3.micro"

  allocated\_storage = 20

  max\_allocated\_storage = 1000

  storage\_type      = "gp2"

  storage\_encrypted = false

  auto\_minor\_version\_upgrade = true

  identifier                = "bookstore"

  username                  = "admin"

  password                  = "12345678"

  publicly\_accessible       = false

  db\_subnet\_group\_name      = aws\_db\_subnet\_group.bookstore\_subnet\_group.name

  vpc\_security\_group\_ids    = \[aws\_security\_group.dbsg.id\]

  skip\_final\_snapshot = true

  tags = {

    Name = "Bookstore-DB"

  }

}

resource "aws\_db\_subnet\_group" "bookstore\_subnet\_group" {

  name       = "bookstore-subnet-group"

  subnet\_ids = \[aws\_subnet.public-sub1.id, aws\_subnet.public-sub2.id\]

}

[**Loadbalancer.tf**](http://Loadbalancer.tf)

* Creating the application load balancer for distributing to web-server of ec2.
    

\# Creating External LoadBalancer

resource "aws\_lb" "external-alb" {

  name               = "PhpLB"

  internal           = false

  load\_balancer\_type = "application"

  security\_groups    = \[aws\_security\_group.jumpsg.id, aws\_security\_group.Websg.id\]

  subnets            = \[aws\_subnet.public-sub1.id, aws\_subnet.public-sub2.id\]

  tags = {

    Name = "Php\_Lb"

  }

}

resource "aws\_lb\_target\_group" "target-group" {

  name     = "bookstore"

  port     = 80

  protocol = "HTTP"

  vpc\_id   = aws\_vpc.php-vpc.id

  health\_check {

    path                = "/index.php"

    interval            = 5

    timeout             = 2

    healthy\_threshold   = 5

    unhealthy\_threshold = 2

    matcher             = "200"

  }

}

resource "aws\_lb\_target\_group\_attachment" "attachement-1" {

  target\_group\_arn = aws\_lb\_target\_group.target-group.arn

  target\_id        = aws\_instance.Web1\[0\].id

  port             = 80

 depends\_on = \[

    aws\_instance.Web1,

  \]

}

resource "aws\_lb\_target\_group\_attachment" "attachment-2" {

  target\_group\_arn = aws\_lb\_target\_group.target-group.arn

  target\_id        = aws\_instance.Web2\[0\].id

  port             = 80

depends\_on = \[

    aws\_instance.Web2,

  \]

}

resource "aws\_lb\_listener" "external-elb" {

  load\_balancer\_arn = aws\_lb.external-alb.arn

  port              = "80"

  protocol          = "HTTP"

  default\_action {

    type             = "forward"

    target\_group\_arn = aws\_lb\_target\_group.target-group.arn

  }

}

\# Output the Load Balancer DNS

output "load\_balancer\_dns" {

  value = aws\_lb.external-alb.dns\_name

}

In this blog, I dive into the essential steps of working with Terraform, an amazing infrastructure as code tool. I cover the following key aspects of the Terraform workflow:

1️⃣ Initialization (**terraform init**): Learn how to set up your Terraform project, configure providers, and download necessary dependencies.

2️⃣ Planning (**terraform plan**): Discover how to generate an execution plan that outlines the changes Terraform will make to your infrastructure.

3️⃣ Validation (**terraform validat**e): Explore the importance of validating your Terraform code to catch any syntax or configuration errors early on.

4️⃣ Application (**terraform apply**): See how to apply your Terraform configuration to provision and manage your infrastructure resources.

5️⃣ Destruction (**terraform destroy**): Understand the process of gracefully tearing down your infrastructure when it's no longer needed.

Now with the help of the above commands we Initialized infrastructure, Validate infrastructure, Plan infrastructure, and finally apply infrastructure.

If u successfully applied the AWS infrastructure using Terraform u will get one load balancer DNS link and paste in the browser you will get the output of "Bookstore" application.

![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiIAeS7NLFyj-VY_YXNQMscBydZNUUAM_NMEnPoR0ietN8wKSou7nM00ml1rpwDBfrm6GoWbMjyhR7nE4q2DGRFTmKBJNE-V-vQt9EDGxcccb0eihND0kg3bdZK-1Xn-C19MxPeY69_VDPjRiofIaVjMSNhhGiZfcBVv8kcKRifV09tiTKh56xLLPAU0A/w418-h193/Screenshot%202023-06-13%20153423.png align="left")

  
  
    What you filled the data here, that data will automatically reflect in mariadb database like this.

![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgfYLU7a48lf2R5HlAf87r7yBYje3CppSLGwxi1XD_LxwWNyiBNMNay-o_-NbEqu9tpfXSueO7Ua9VFHnKAlQk5UtjIWly0rTrqPCQJXxCgMTm2RnBN_OsFXQTf-1SLz5TTGsqbRoJo7NX1s7pel5kkLtKM1Myw9xWu3WDr2ggEL5iP9D06TBmvzhgp4w/w434-h164/WhatsApp%20Image%202023-06-12%20at%2022.50.27.jpg align="left")

Thank you for reading my block.

That's fantastic! Successfully completing the second part of your blog on the 3-tier application on AWS with Terraform.

Thank you for reading this blog. if u like this content,

Follow me on Linkedin; [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)

Follow on Whatsapp: [https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3](https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3)

Follow on telegram: [https://t.me/awsdevopscontent](https://t.me/awsdevopscontent)