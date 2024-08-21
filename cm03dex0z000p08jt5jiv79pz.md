---
title: "Terraform Made Easy: A Guide to Variables, tfvars, and Locals"
datePublished: Wed Aug 21 2024 04:45:39 GMT+0000 (Coordinated Universal Time)
cuid: cm03dex0z000p08jt5jiv79pz
slug: terraform-made-easy-a-guide-to-variables-tfvars-and-locals
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1724215492152/13c84f8c-c1c7-4521-85b4-94660397d309.png
tags: devops, terraform, devops-articles, terraform-state, terraweekchallenge

---

## 🌍 Terraform in DevOps: Simplifying `variable.tfvars`, [`variable.tf`](http://variable.tf), and `locals`

Terraform is a must-know tool for anyone in DevOps, helping you automate and manage infrastructure with ease. But when you start using Terraform, you might find yourself puzzled by different ways to handle variables. You’ll encounter terms like [`variable.tf`](http://variable.tf), `variable.tfvars`, and `locals`. What do these mean, and how do you use them? Let's break it down in a way that’s easy to understand.

### 🤔 What is Terraform?

Terraform, created by HashiCorp, is a tool that lets you define and manage your infrastructure as code 🧑‍💻. Instead of manually setting up servers, databases, or networks, you write everything in configuration files using a language called HCL (HashiCorp Configuration Language). Terraform then turns these configurations into actual infrastructure in your cloud environment ☁️.

### ❓ Why Do Variables Matter?

Imagine you’re setting up multiple environments—like development, staging, and production 🌱🚀. Each environment might need slightly different settings. Instead of copying and pasting your configurations with minor tweaks, you can use variables to make your code reusable and flexible.

### 📝 [`variable.tf`](http://variable.tf): Defining Your Variables

Think of [`variable.tf`](http://variable.tf) as the place where you create placeholders for the values you’ll need later 🏗️. These placeholders are called variables. In this file, you set up the rules for each variable: what type it is, what it does, and what default value it should have if no other value is given.

#### Example:

```json
# variable.tf
variable "instance_type" {
  description = "Type of instance to use"
  type        = string
  default     = "t2.micro"
}

variable "instance_count" {
  description = "Number of instances to create"
  type        = number
}
```

* `instance_type` is like saying, "I might want to change the type of server I use, but if I don’t specify, just use `t2.micro`." 🖥️
    
* `instance_count` is saying, "Tell me how many servers you want, but there’s no default, so you have to specify this." 🔢
    

### 🛠️ `variable.tfvars`: Setting the Values

While [`variable.tf`](http://variable.tf) defines the variables, `variable.tfvars` is where you actually assign the values to these variables. It’s like filling in the blanks ✍️.

#### Example:

```json
# variable.tfvars
instance_type  = "t3.medium"
instance_count = 3
```

Here, we’re saying, "For this specific run, I want to use `t3.medium` servers, and I want three of them." This file allows you to easily switch values without changing the underlying configuration 🔄.

#### 🚀 How to Use:

When you run Terraform, you can tell it to use the values from your `variable.tfvars` file like this:

```json
terraform apply -var-file="variable.tfvars"
```

### ♻️ `locals`: Reusing Values

Sometimes you need to calculate or define values based on other variables. That’s where `locals` come in 🔗. `locals` let you create new values by combining or transforming existing ones, making your code more efficient and less repetitive.

#### Example:

```json
# locals.tf
locals {
  instance_name = "${var.instance_type}-instance"
  tags = {
    Name        = "MyApp-${var.instance_type}"
    Environment = "Production"
  }
}
```

* `instance_name` might generate a name like `"t3.medium-instance"` based on the `instance_type` you set 🏷️.
    
* `tags` create labels for your resources, which might look like `{"Name": "MyApp-t3.medium", "Environment": "Production"}`.
    

### 🔗 Putting It All Together

Let’s say you’re creating an EC2 instance in AWS ☁️. You could define the instance type and count in [`variable.tf`](http://variable.tf), set the actual values in `variable.tfvars`, and then use `locals` to create a custom name and tags for each instance.

#### Example:

```json
resource "aws_instance" "example" {
  instance_type = var.instance_type
  count         = var.instance_count

  tags = local.tags
}
```

Here’s what’s happening:

* Terraform looks in [`variable.tf`](http://variable.tf) to see what variables are available 🔍.
    
* It then looks in `variable.tfvars` to see what values you’ve provided 🗂️.
    
* Finally, it uses `locals` to generate any extra details it needs 🛠️.
    

### 📊 Comparing [`variable.tf`](http://variable.tf), `variable.tfvars`, and `locals`

* [`variable.tf`](http://variable.tf): Defines what variables exist and what they do. It’s like the blueprint for your variables 🧩.
    
* `variable.tfvars`: Provides the actual values for those variables. It’s where you tell Terraform what specific settings to use 🎯.
    
* `locals`: Helps you create new, reusable values based on your variables, reducing repetition and keeping your code clean 🧼.
    

### 📚 Best Practices

1. **Define variables clearly in** [`variable.tf`](http://variable.tf): This keeps your configuration organized 📋.
    
2. **Use separate** `.tfvars` files for different environments: This makes it easy to switch between settings for development, staging, and production 🚀.
    
3. **Use** `locals` to simplify your configuration: This avoids repetition and makes your code easier to manage 🧹.
    

### 🏁 Conclusion

Understanding the role of [`variable.tf`](http://variable.tf), `variable.tfvars`, and `locals` in Terraform will make your configurations more flexible, reusable, and easier to manage. By following these guidelines, you can streamline your infrastructure management and make your Terraform code both powerful and clean ✨.

I hope you people like this blog.

If you like this blog please follow these below Links, You will get more content like this in that links.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695627131885/d3899b2c-dd76-4ef9-8230-870760b10aac.gif align="left")

WhatsApp Group:- [https://chat.whatsapp.com/Ii2xKz9vuW93AWt07m4AYj](https://chat.whatsapp.com/Ii2xKz9vuW93AWt07m4AYj)

Telegram:- [https://t.me/ExplorewithAshok](https://t.me/ExplorewithAshok)

LinkedIn: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)

Instagram:- [https://instagram.com/explorewithashok?igshid=OGQ5ZDc2ODk2ZA==](https://instagram.com/explorewithashok?igshid=OGQ5ZDc2ODk2ZA==)

Linktree:- [https://linktr.ee/ashoksana](https://linktr.ee/ashoksana)