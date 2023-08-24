---
title: "Unlocking the Power of Wal2Json in Ubuntu with PostgreSQL"
datePublished: Mon Jul 24 2023 13:33:54 GMT+0000 (Coordinated Universal Time)
cuid: clkgwsm50000c0al4aujr4nfq
slug: unlocking-the-power-of-wal2json-in-ubuntu-with-postgresql
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690205419879/aac00ff0-fdee-49c0-9ee4-a5cb9d008bcf.png
tags: ubuntu, postgresql, aws, wal2json

---

**What is Wal2Json?**

Wal2Json is a remarkable plugin designed for PostgreSQL that opens up new possibilities by enabling logical replication. It stands for "Write-Ahead Logging to JSON," and as the name suggests, it generates JSON output from the Write-Ahead Logs (WAL) in PostgreSQL. This innovative feature allows developers to extract, transform, and consume data in a structured format, making it highly versatile and useful.

**Why Do We Use Wal2Json?**

In the world of database management, replication is crucial for data redundancy, high availability, and data distribution across multiple servers. Traditional physical replication replicates the entire database cluster, which may not be suitable for all scenarios, especially when you want to replicate specific data subsets or apply transformations during replication.

This is where logical replication, empowered by Wal2Json, comes into play. Unlike physical replication, logical replication replicates data based on the logical changes made to the database, such as INSERTs, UPDATEs, and DELETEs, in the form of WAL records.

**How is Wal2Json Useful to Us?**

Wal2Json opens up a realm of possibilities for developers and database administrators:

1. **Selective Replication:** With logical replication, you can choose to replicate only specific tables or even specific columns within tables, tailoring replication to your specific needs.
    
2. **Data Transformation:** The JSON output from Wal2Json allows you to apply data transformations during replication, facilitating data integration with other systems.
    
3. **Change Data Capture (CDC):** Wal2Json's JSON output serves as an excellent source for capturing and analyzing changes made to the database, providing insights into the data evolution.
    
4. **Real-Time Data Synchronization:** Logical replication enables real-time synchronization of data between databases, making it ideal for scenarios like multi-datacenter setups or sharding.
    
5. **Easier Data Consumption:** The JSON format simplifies data consumption and integration with various applications and tools that understand JSON natively.
    

**Main Purpose of Wal2Json:**

The main purpose of Wal2Json is to enable logical replication in PostgreSQL and provide a streamlined, efficient, and flexible way to replicate and consume data changes. By converting WAL records into JSON format, Wal2Json allows you to harness the power of logical replication to meet diverse data replication and consumption requirements.

With Wal2Json, PostgreSQL becomes even more valuable for scenarios where precise data replication, transformation, and real-time synchronization are paramount. It empowers developers and database administrators to tailor replication to their specific needs and build robust, scalable, and data-driven applications.

🚀 **Step 1: Installing Postgresql in Ubuntu** 🚀

To begin our journey, we need to install Postgresql from the PostgreSQL official website. Select Linux and Ubuntu

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690199689038/763d392c-fc4b-4930-b520-39a9589d8b20.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690199750435/e637dc9b-a7ea-4da2-9648-b2fd67861cec.png align="center")

Run below following commands

```bash
$sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
$wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
$sudo apt-get update
$sudo apt-get -y install postgresql-14
$psql --version
```

Then clone the wal2json repository.

repository.

```bash
$ sudo apt-get install git -y
$ sudo git clone https://github.com/Ashoksana/wal2json.git
```

🔒 **Step 2: Installing Wal2Json Plugin** 🔒

we need to install the Wal2Json package from the PostgreSQL apt repository.

```bash
$ sudo apt-get install postgresql-14-wal2json
```

🔒**Step 2: Securing Your PostgreSQL Database** 🔒

Let's set a password for the PostgreSQL user "postgres" to ensure our database's security.

```bash
$ sudo –u postgres psql –c “ALTER USER postgres PASSWORD ‘<password>’;”
```

⚙️ **Step 3: Configuring PostgreSQL Parameters** ⚙️

To enable logical replication, we must tweak some parameters in the "postgresql.conf" file.

```bash
$ cd /etc/postgresql/14/main
$ sudo nano postgresql.conf
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690202059938/a31ef39f-fb8f-4251-8fc2-cda97d3899d0.png align="center")

Edit the following parameters:

```bash
wal_level = logical
max_replication_slots = 10
max_wal_senders = 10
```

Save the changes (Ctrl + S) and exit (Ctrl + X).

Now, restart PostgreSQL to apply the changes.

```bash
$ sudo systemctl restart postgresql
```

🔐 **Step 4: Add Replication Connection Rule** 🔐

In the "pg\_hba.conf" file, we'll define a replication connection rule.

```bash
$ sudo nano pg_hba.conf
```

Edit the following line:

```bash
#Database adminstrative login by Unix domain socket
local all postgres     md5
local all all          trust
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690200913680/ffa7a57e-3379-4040-a8e7-f73f10dbe570.png align="center")

Save the changes.

Now, restart PostgreSQL again.

```bash
$ sudo systemctl restart postgresql
```

💻 **Step 5: Trying Out Wal2Json** 💻

In one terminal window, create a logical replication slot using the "pg\_recvlogical" utility.

```bash
$ pg_recvlogical -d postgres --slot test_slot --create-slot -P wal2json -U postgres -W
```

In the same terminal, start the logical replication using the same utility.

```bash
$ pg_recvlogical -d postgres --slot test_slot --start -o pretty-print=1 -o add-msg-prefixes=wal2json -f - -U postgres
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690202160600/e8c4850d-b1d4-43d8-b129-e4b3f1ca3eee.png align="center")

📄 **Step 6: Executing SQL Commands** 📄

In another terminal window, create a file (e.g., "example1.sql") and paste the SQL commands you want to test with Wal2Json.

```bash
$ cat /tmp/example1.sql
CREATE TABLE table1_with_pk (a SERIAL, b VARCHAR(30), c TIMESTAMP NOT NULL, PRIMARY KEY(a, c));
CREATE TABLE table1_without_pk (a SERIAL, b NUMERIC(5,2), c TEXT);

BEGIN;
INSERT INTO table1_with_pk (b, c) VALUES('Backup and Restore', now());
INSERT INTO table1_with_pk (b, c) VALUES('Tuning', now());
INSERT INTO table1_with_pk (b, c) VALUES('Replication', now());
SELECT pg_logical_emit_message(true, 'wal2json', 'this message will be delivered');
SELECT pg_logical_emit_message(true, 'pgoutput', 'this message will be filtered');
DELETE FROM table1_with_pk WHERE a < 3;
SELECT pg_logical_emit_message(false, 'wal2json', 'this non-transactional message will be delivered even if you rollback the transaction');

INSERT INTO table1_without_pk (b, c) VALUES(2.34, 'Tapir');
-- it is not added to stream because there isn't a pk or a replica identity
UPDATE table1_without_pk SET c = 'Anta' WHERE c = 'Tapir';
COMMIT;

DROP TABLE table1_with_pk;
DROP TABLE table1_without_pk;
```

```bash
$ nano /tmp/example1.sql
```

Enter the SQL commands and save the file (Ctrl + S) and exit (Ctrl + X).

Next, execute the SQL commands in the file using the "psql" utility.

```bash
$ psql -At -f /tmp/example1.sql postgres -U postgres
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690201884038/46fa6acf-4304-4842-9da7-d205e6ee15ee.png align="center")

🎉 **Step 7: Witness the Magic of Wal2Json** 🎉

In the terminal where we started logical replication, you'll see the actual JSON output generated from the WAL.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690202536961/92805dee-9809-4e9c-a1ef-0c55b9e7feb8.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690202562855/dd126178-fe2d-42d8-8dc2-2825ed9e4be0.png align="center")

If you want a Time-stamp of every query, update download the source code of wal2json, and edit the flag variable.

Here write it as True and will get the output of the timestamp of every query, update, delete...

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690203070093/4b582e0b-bd20-41ee-998d-8ac568d46b2b.png align="center")

Then you will get the output along with time of query, update, delete.....

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690204198159/96d2dbce-4ef8-4454-8a7e-74bf031ef64c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690204235973/5d764365-d8f8-4291-ba91-66e4a709fd87.png align="center")

You've successfully explored the world of Wal2Json in Ubuntu with PostgreSQL. Harness the power of logical replication and JSON output for more efficient data handling. Happy coding and replication! 🚀🔥

Feel free to ask any questions or share your thoughts in the comments below! 😊👍

Hope you like my blog...!

Ashok Sana  
Follow me on Linkedin: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)