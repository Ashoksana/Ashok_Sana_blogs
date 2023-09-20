---
title: "Exploring Bazel: How I Built a High-Performance Java Calculator"
datePublished: Wed Sep 20 2023 07:50:18 GMT+0000 (Coordinated Universal Time)
cuid: clmrg25gq000509mgem3m782e
slug: exploring-bazel-how-i-built-a-high-performance-java-calculator
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695196167703/e6df42b9-0d19-4ffe-a99f-67397b097f4b.png
tags: ubuntu, bazel, java, 90daysofdevops

---

![Bazel](https://www.gstatic.com/devrel-devsite/prod/v034be4d3466fb3986ffa351f14a2dec43335ca06535087890c303c3b2bda2be0/bazel/images/lockup.svg align="left")

## **What is Bazel? 🤔**

Bazel is an open-source build and test tool developed by Google. It's designed to build, test, and package software efficiently across different programming languages and platforms. 🌐💻 Bazel provides a uniform and reproducible way to manage dependencies and build artifacts, making it an ideal choice for DevOps teams seeking performance and scalability.

### **Highlights**

* 🚀 Bazel is a blazing-fast build tool used by major companies for its speed and reproducibility.
    
* 🛠️ Define inputs and outputs to model code dependencies and rebuild only when necessary.
    
* 📦 Create packages and build files to specify targets and commands for building code.
    
* 💡 Use macros to simplify complex build steps and reuse code across projects.
    
* 🌐 Explore advanced features like testing, dependency graph generation, and integration with CI/CD pipelines.
    

### **Why Bazel? 🤔**

🔸 **Fast Builds:** Bazel's incremental build system ensures only the necessary parts of your project are rebuilt, saving valuable time.

🔸 **Cross-Language Support:** It supports multiple programming languages, making it versatile for heterogeneous codebases.

🔸 **Scalability:** Bazel scales effortlessly, making it ideal for large and complex projects.

🔸 **Reproducibility:** Achieve consistent builds across different environments, ensuring that what works locally works in production.

### **BAZEL Vs MAVEN Vs Gradle**

<table><tbody><tr><td colspan="1" rowspan="1"><p>Aspect</p></td><td colspan="1" rowspan="1"><p>Bazel</p></td><td colspan="1" rowspan="1"><p>Maven</p></td><td colspan="1" rowspan="1"><p>Gradle</p></td></tr><tr><td colspan="1" rowspan="1"><p>Language Support</p></td><td colspan="1" rowspan="1"><p>Multiple languages (Java, C++, Python, etc.)</p></td><td colspan="1" rowspan="1"><p>Primarily Java-centric</p></td><td colspan="1" rowspan="1"><p>Supports various languages (Java, Kotlin, Groovy, etc.)</p></td></tr><tr><td colspan="1" rowspan="1"><p>Performance</p></td><td colspan="1" rowspan="1"><p>Faster, thanks to incremental builds</p></td><td colspan="1" rowspan="1"><p>Slower for larger projects</p></td><td colspan="1" rowspan="1"><p>Slower for large projects</p></td></tr><tr><td colspan="1" rowspan="1"><p>Reproducibility</p></td><td colspan="1" rowspan="1"><p>Strong, with hermetic builds</p></td><td colspan="1" rowspan="1"><p>Less control over dependencies</p></td><td colspan="1" rowspan="1"><p>Limited control over dependencies</p></td></tr><tr><td colspan="1" rowspan="1"><p>Scalability</p></td><td colspan="1" rowspan="1"><p>Scales effortlessly</p></td><td colspan="1" rowspan="1"><p>N/A</p></td><td colspan="1" rowspan="1"><p>Suitable for medium-sized projects</p></td></tr></tbody></table>

### **Language Support:**

#### Bazel Example:

```yaml
py_binary(
    name = "my_python_app",
    srcs = ["main.py"],
)
cc_binary(
    name = "my_cpp_app",
    srcs = ["main.cpp"],
)
```

#### Maven Example (Java):

```yaml
xmlCopy code<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>my-java-app</artifactId>
    <version>1.0</version>
</project>
```

#### Gradle Example (Kotlin):

#### Gradle Example (Kotlin):

```kotlin
plugins {
    id("org.jetbrains.kotlin.jvm") version "1.5.20"
}

repositories {
    mavenCentral()
}

dependencies {
    implementation(kotlin("stdlib"))
}
```

### **Installation of Bazel in Ubuntu.**

Step - 1:

Go to the Official website [https://bazel.build/](https://bazel.build/) click on install bazel

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695099742474/8c1a9fbe-7daa-43ec-ae9d-9cb9c29b4749.png align="center")

### Follow the documentation to install bazel

#### Bazel Example:

```bash
sudo apt install apt-transport-https curl gnupg -y
curl -fsSL https://bazel.build/bazel-release.pub.gpg | gpg --dearmor >bazel-archive-keyring.gpg
sudo mv bazel-archive-keyring.gpg /usr/share/keyrings
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/bazel-archive-keyring.gpg] https://storage.googleapis.com/bazel-apt stable jdk1.8" | sudo tee /etc/apt/sources.list.d/bazel.list
sudo apt update && sudo apt install bazel -y
sudo apt update && sudo apt full-upgrade
bazel --version
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695104496444/58ebf110-aed5-47a4-89ec-cd4727add815.png align="center")

### **Installation of Bazel in Windows.**

First open Windows power shell or Command Prompt as administrative user and follow below commands.

```basic
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
choco install bazelisk
bazel --version
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695188557108/3ae90036-a849-46f9-879d-563bcb68555d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695188588841/2c4b89d0-8b45-42be-b5f0-af84824a77c7.png align="center")

### **Build application in Ubuntu os**

After installation bazel in ubuntu os, now we try to build java sample application using bazel

First install java in your ubuntu os using following command:  
`sudo apt install openjdk-11-jdk`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695107023123/5b3b69c3-7d52-40d0-b832-907f4aa5d452.png align="center")

### These are bazel commands for executions, run, build...

<table><tbody><tr><td colspan="1" rowspan="1"><p>bazel build &lt;target&gt;</p></td><td colspan="1" rowspan="1"><p>Build the specified target(s) and their dependencies.</p></td><td colspan="1" rowspan="1"><p>bazel build //path/to:target</p></td></tr><tr><td colspan="1" rowspan="1"><p>bazel test &lt;target&gt;</p></td><td colspan="1" rowspan="1"><p>Build and run tests for the specified target(s).</p></td><td colspan="1" rowspan="1"><p>bazel test //path/to:target</p></td></tr><tr><td colspan="1" rowspan="1"><p>bazel run &lt;target&gt;</p></td><td colspan="1" rowspan="1"><p>Build and run the specified target.</p></td><td colspan="1" rowspan="1"><p>bazel run //path/to:target</p></td></tr><tr><td colspan="1" rowspan="1"><p>bazel clean</p></td><td colspan="1" rowspan="1"><p>Delete build output files and directories.</p></td><td colspan="1" rowspan="1"><p>bazel clean</p></td></tr><tr><td colspan="1" rowspan="1"><p>bazel query &lt;query&gt;</p></td><td colspan="1" rowspan="1"><p>Query the build graph to find targets.</p></td><td colspan="1" rowspan="1"><p>bazel query 'deps(//path/to:target)'</p></td></tr><tr><td colspan="1" rowspan="1"><p>bazel info &lt;key&gt;</p></td><td colspan="1" rowspan="1"><p>Display information about the build configuration.</p></td><td colspan="1" rowspan="1"><p>bazel info execution_root</p></td></tr><tr><td colspan="1" rowspan="1"><p>bazel fetch &lt;target&gt;</p></td><td colspan="1" rowspan="1"><p>Fetch external dependencies for a target.</p></td><td colspan="1" rowspan="1"><p>bazel fetch @maven//:com_google_guava_guava</p></td></tr><tr><td colspan="1" rowspan="1"><p>bazel version</p></td><td colspan="1" rowspan="1"><p>Display Bazel version information.</p></td><td colspan="1" rowspan="1"><p>bazel version</p></td></tr><tr><td colspan="1" rowspan="1"><p>bazel help &lt;command&gt;</p></td><td colspan="1" rowspan="1"><p>Display help information for a specific command.</p></td><td colspan="1" rowspan="1"><p>bazel help build</p></td></tr></tbody></table>

For example, if you have a Java target in the path //src/main/java/com/example:HelloWorld, you would use the following commands:

To build: bazel build //src/main/java/com/example:HelloWorld To test: bazel test //src/main/java/com/example:HelloWorld To run: bazel run //src/main/java/com/example:HelloWorld

### Now we build one simple java calculator application with Bazel tool in Ubuntu os

After Installation of Bazel and java in Ubuntu, then create below folder structure

Make sure your project directory structure looks like this:

1. ```basic
     java_calculator/
     ├── WORKSPACE
     ├── BUILD
     └── Calculator.java
    ```
    
    In "BUILD.bazel" file write your actions like this
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695192365780/1d0cd259-ecde-481f-9913-5b3626944d95.png align="center")
    
    Update the `BUILD` file content as follows:
    
    ```python
    java_binary(
        name = "calculator",
        srcs = ["Calculator.java"],
        main_class = "Calculator",
    )
    ```
    
    * `java_binary`: This is a Bazel build rule. In this context, it represents a Java binary target. It tells Bazel that you want to create a binary executable from Java source code.
        
    * `name = "calculator"`: This attribute sets the **name of the build target**. The target is named "calculator." You will use this name to refer to the target elsewhere in your Bazel configuration or when running Bazel commands.
        
    * `srcs = ["`[`Calculator.java`](http://Calculator.java)`"]`: This attribute specifies the **source files** needed to build the Java binary. In this case, there is a single source file named "[Calculator.java](http://Calculator.java)." Bazel will compile this Java source file to create the binary executable.
        
    * `main_class = "Calculator"`: This attribute specifies the **main class** of your Java application. When you run the binary executable, Bazel will look for the `main` method in the "Calculator" class and execute it. This attribute is essential because it determines the entry point of your Java program.
        
    
    Here we use "BUILD" file in BAZEL are
    
    🎯 Purpose of a BUILD File in Bazel:
    
    **🏗️ Define Targets:** BUILD files allow you to define build targets, which are individual components or artifacts that Bazel can build.
    
    **📝 Specify Build Instructions:** You can specify how these targets should be built, including compilation, testing, and packaging.
    
    **🧩 Manage Dependencies:** BUILD files help you manage dependencies between different components of your project.
    
    **🧱 Structure Your Project:** They are crucial for structuring your project and organizing it into manageable pieces.
    
    **🚀 Build Automation:** Bazel uses these files to automate the build process and ensure consistency.
    
    **🕵️ Declarative:** They provide a declarative way to describe your project's build requirements, making it clear and easy to understand.
    
    1. You can name the target anything you like (e.g., "calculator"). Make sure to create a Java source file [`Calculator.java`](http://Calculator.java) in the same directory:
        
        ```java
        javaCopy code// Calculator.java
        public class Calculator {
            public static void main(String[] args) {
                if (args.length != 3) {
                    System.out.println("Usage: Calculator <num1> <operator> <num2>");
                    return;
                }
                double num1 = Double.parseDouble(args[0]);
                String operator = args[1];
                double num2 = Double.parseDouble(args[2]);
                double result = 0.0;
                switch (operator) {
                    case "+":
                        result = num1 + num2;
                        break;
                    case "-":
                        result = num1 - num2;
                        break;
                    case "*":
                        result = num1 * num2;
                        break;
                    case "/":
                        if (num2 != 0) {
                            result = num1 / num2;
                        } else {
                            System.out.println("Error: Division by zero.");
                            return;
                        }
                        break;
                    default:
                        System.out.println("Error: Invalid operator.");
                        return;
                }
                System.out.println("Result: " + result);
            }
        }
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695193044685/d9694421-e57a-49c3-9644-1e5c2206434e.png align="center")
        
        And also create "WORKSPACE.bazel" file for
        
        📦 **Dependency Management**: The `WORKSPACE` file specifies external dependencies (libraries, frameworks, etc.) your project needs to build and run.
        
        🔗 **Repository Rules**: It uses rules (like Git, HTTP, Maven) to fetch and manage external code.
        
        🛠️ **Toolchains Configuration**: You set up toolchains for different languages/platforms (e.g., Java JDK version).
        
        🏭 **Workspace Setup**: Ensures a consistent environment with all required dependencies for building your project.
        
        ⚙️ **Workspace-wide Settings**: You define project-wide settings (code formatting, testing) for everyone.
        
        🌐 **Third-Party Code Integration**: Structured way to declare and manage third-party dependencies.
        
        The `WORKSPACE` file streamlines your project's setup, management, and collaboration with external code and resources.
        
        <mark>Here we created a "WORKSPACE" file but we did not insert anything in that file because there is no external dependencies or specific toolchain configurations in the </mark> `WORKSPACE` <mark>file. This is perfectly fine and is not always necessary.</mark>
        
        Finally, this is java\_calculator dir structure as mentioned picture.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695193788855/a9857a8d-41ff-4f53-85d8-1fb9f73d4ec8.png align="center")
        
        Then, you build your application following bazel command
        
        1. Build your Java calculator application:
            
            ```bash
            cd java_calculator
            sudo bazel build :calculator_deploy.jar
            ```
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695194055320/4ee18b49-0f15-49df-a169-52558a3bc2ab.png align="center")
            
            Finally java application is build with bazel tool, After this it will create some bazel files.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695194174170/65707225-69eb-4cea-904a-e64156f824c4.png align="center")
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695194212642/a2c32466-dbc2-4afb-b7ec-6558297486f7.png align="center")
            
            If you want to output for this java\_calculator follow this commands
            
            **Run the JAR file:** Finally, try running the JAR file with the `java -jar` command:
            
            ```bash
            sudo java -jar bazel-bin/calculator_deploy.jar 5 + 3
            sudo java -jar bazel-bin/calculator_deploy.jar 5 / 3
            sudo java -jar bazel-bin/calculator_deploy.jar 5 - 3
            ```
            
            Finally we build java simple calculator application using Bazel. You guys try this in Windows
            
        
        Hope you like my blog...!
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692351695778/c9653064-2cfb-48eb-9cf3-9fcc3a16bfe7.png align="center")
        
        If you like the content follow me on LinkedIn: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)
        
        Follow my Whatsapp & telegram community: [https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3](https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3)
        
        [https://t.me/ExplorewithAshok](https://t.me/ExplorewithAshok)
        
        Happy learning......!