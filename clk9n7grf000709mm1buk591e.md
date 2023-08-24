---
title: "Advanced Linux BashShell Scripting for DevOps Engineers."
datePublished: Wed Jul 19 2023 11:31:07 GMT+0000 (Coordinated Universal Time)
cuid: clk9n7grf000709mm1buk591e
slug: advanced-linux-bashshell-scripting-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689766200397/16631f06-5170-4c8d-9f3b-78b655abb1e3.png
tags: linux, linux-for-beginners, bash-shell-script, advance-linux-scripting

---

**Introduction:**

Hey there! Welcome to the wacky world of Bash scripting. 🎉 Get ready to dive into a series of hilarious examples and explore the wild possibilities of the command line. 🚀

## **01\_05 Bash expansions and substitutions**

Let's start our bash journey with some mind-blowing expansions and substitutions. Brace yourself! 🤓

```bash
echo ~ 😄
echo ~- 🤔
```

## **01\_06 Brace expansion**

Now, let's have some fun with brace expansion. Brace yourself for the unexpected! 😜

```bash
echo {1..10} 😲
echo {10..1} 😯
echo {01..10} 😎
echo {01..100} 😵
echo {a..z} 😃
echo {Z..A} 😅
echo {1..30..3} 😄
echo {a..z..2} 😆
touch file_{01..12}{a..d} 😂
echo {cat,dog,fox} 🐱🐶🦊
echo {cat,dog,fox}_{1..5} 😸🐶🦊
```

## **01\_07 Parameter expansion**

Let's play around with parameter expansion. It's like magic, but with dollar signs! 🪄✨

```bash
$Proposing="I love You"
echo $Proposing 🤗
echo ${Proposing:6} 🙋‍♂️
echo ${Proposing:6:3} 😊
echo ${Proposing/you/everybody} 🤝
echo ${Proposing//o/_} 🤐
echo ${Proposing/o/_} 🤫
echo $Proposing:4:3 😮
```

## **01\_08 Command substitution**

Time to dive into command substitution. Let's mix commands with our witty remarks! 💬💡

```bash
$uname -r 🖥️
echo "The kernel is $(uname -r)." 💻
echo "Result: $(python3 -c 'print("Hello from Python!")' | tr [a-z] [A-Z])" 🐍
```

## **01\_09 Arithmetic expansion**

Get your calculators ready because we're about to crunch some numbers! 🔢🧮

```bash
echo $(( 2 + 2 )) 🤓
echo $(( 4 - 2 )) 😄
echo $(( 4 * 5 )) 😎
echo $(( 4 / 5 )) 😯
```

## **02\_01 Understanding Bash script syntax**

Now, let's explore the basic syntax of a Bash script. Prepare to have your mind blown! 💥

```bash
nano myscript / vi myscript / vim myscript
#!/usr/bin/env bash
echo "hello" 😄
# This is a comment
echo "there" 👋
chmod +x myscript
./myscript 🏃‍♂️
```

## **02\_03 Displaying text with 'echo'**

Let's have a blast with the 'echo' command and make some bold statements! 💪📢

```bash
echo Ashok is sharing knowledge 👋🌍
explorewithashok=devops
echo Ashok is sharing knowledge on $explorewithashok 👋🌎
echo "The kernel is $(uname -r)" 🖥️
echo The kernel is $(uname -r) 🖥️
echo The (kernel) is $(uname -r) 🤔
echo The \(kernel\) is $(uname -r) 😄
echo 'The kernel is $(uname -r)' 🖥️
echo "The (kernel) is $(uname -r)" 🤔
echo "The (kernel) is \$(uname -r)" 😆
echo
echo; echo "More space!"; echo
echo -n "No newline" ❌↩️
echo -n "Part of "; echo -n "a statement" 👊📜
```

## **02\_04 Working with variables**

Time to unleash the power of variables! Get ready to store some information! 📦💡

```bash
#!/bin/bash
Author=Ashok
Age=26
Intererested_in="Devops"
echo $Author 😃
echo $Age 😄
echo $Interested_in 😎
```

```bash
#!/bin/bash
myvar="Hello!"
echo "The value of the myvar variable is: $myvar" 🤗
myvar="people"
echo "The value of the myvar variable is: $myvar" 😊
declare -r myname="Ashok"
echo "The value of the myname variable is: $myname" 🤐
myname="Sana"
echo "The value of the myname variable is: $myname" 😮
declare -l lowerstring="This is some TEXT!"
echo "The value of the lowerstring variable is: $lowerstring" 📜
lowerstring="Let's CHANGE the VALUE!"
echo "The value of the lowerstring variable is: $lowerstring" 😅
declare -u upperstring="This is some TEXT!"
echo "The value of the upperstring variable is: $upperstring" 📜
upperstring="Let's CHANGE the VALUE!"
echo "The value of the upperstring variable is: $upperstring" 😄
```

```bash
declare -p 📦
env 🌍
echo $USER 👤
```

## **02\_05 Working with numbers**

Let's have some numerical fun! Prepare for calculations and random surprises! 🔢🎲

```bash
echo $((4+4)) 🤓
echo $((8-5)) 😄
echo $((2*3)) 😎
echo $((8/4)) 😯
echo $(( (3+6) - 5 * (5-2) )) 😲
a=3
((a+=3))
echo $a 😄
((a++))
echo $a 😆
((a++))
echo $a 🙃
((a--))
echo $a 🤪
(($a++))
((a++))
echo $a 😂
a=$a+2
echo $a 😅
declare -i b=3
b=$b+3
echo $b 🧮
echo $((1/3)) 🤔
declare -i c=1
declare -i d=3
e=$(echo "scale=3; $c/$d" | bc)
echo $e 🧪
echo $RANDOM 🎲
echo $(( 1 + $RANDOM % 10 )) 🤪
echo $(( 1 + $RANDOM % 20 )) 🤪
```

## **02\_06 Comparing values with test**

Time to put our detective hats on and compare values like pros! 👮‍♂️🔍

```bash
help test ❓
[ -d ~ ] 📁
echo $? 🤔
[ -d /bin/bash ]; echo $? 📁
[ -d /bin ]; echo $? 📁
[ "cat" = "dog" ]; echo $? ❌
[ "cat" = "cat" ]; echo $? ✅
[ 4 -lt 5 ]; echo $? ✅
[ 4 -lt 3 ]; echo $? ❌
[ ! 4 -lt 3 ]; echo $? ✅
```

## **02\_07 Comparing values with extended test**

Let's level up our comparisons with extended tests! Get ready for some advanced detective work! 👮‍♂️🔬

```bash
[[ 4 -lt 3 ]]; echo $? ❌
[[ -d ~ && -a /bin/bash ]]; echo $? 📁✅
[[ -d ~ && -a /bin/mash ]]; echo $? 📁❌
[[ -d ~ || -a /bin/bash ]]; echo $? ✅
[[ -d /bin/bash ]] && echo ~ is a directory 📁
ls && echo "listed the directory" 🗂️
true && echo "success!" ✅
false && echo "success!" ❌
[[ "cat" =~ c.* ]]; echo $? ✅
[[ "bat" =~ c.* ]]; echo $? ❌
```

## **02\_08 Formatting and styling text output**

Time to get fancy with our text output! Let's add some style and flair! 💅🌟

```bash
echo -e "Name\t\tNumber"; echo -e "Scott\t\t123" 📋
echo -e "This text\nbreaks over\nthree lines" 📜
echo -e "\a" 🔔
echo -e "Ding\a" 🔔
```

```bash
#!/bin/bash
echo -e "\033[33;44mColor Text\033[0m" 🎨
echo -e "\033[30;42mColor Text\033[0m" 🎨
echo -e "\033[41;105mColor Text" 🎨
echo "some text that shouldn't have styling" 💬
echo -e "\033[0m" 🎨
echo "some text that shouldn't have styling" 💬
echo -e "\033[4;31;40mERROR:\033[0m\033[31;40m Something went wrong.\033[0m" 🚨❌
```

```bash
#!/bin/bash
ulinered="\033[4;31;40m"
red="\033[31;40m"
none="\033[0m"
echo -e $ulinered"ERROR:"$none$red" Something went wrong."$none 🚨❌
```

## **02\_09 Formatting output with printf**

Time to become a formatting genius with the mighty printf command! Prepare for elegance! 🎩✨

```bash
echo "The results are: $(( 2 + 2 )) and $(( 3 / 1 ))" 🧮
printf "The results are: %d and %d\n" $(( 2 + 2 )) $(( 3 / 1 )) 🧮
```

```bash
#!/bin/bash
echo "----10----| --5--" 📋
echo "Right-aligned text and digits" 📋
printf "%10s: %5d\n" "A Label" 123 "B Label" 456 🧮
echo "Left-aligned text, right-aligned digits" 📋
printf "%-10s: %5d\n" "A Label" 123 "B Label" 456 📋
echo "Left-aligned text and digits" 📋
printf "%-10s: %-5d\n" "A Label" 123 "B Label" 456 📋
echo "Left-aligned text, right-aligned and padded digits" 📋
printf "%-10s: %05d\n" "A Label" 123 "B Label" 456 📋
echo "----10----| --5--" 📋
```

```bash
printf "%(%Y-%m-%d %H:%M:%S)T\n" 1658179558 ⌛
date +%s ⌛
date +%Y-%m-%d\ %H:%M:%S ⌛
printf "%(%Y-%m-%d %H:%M:%S)T\n" $(date +%s) ⌛
printf "%(%Y-%m-%d %H:%M:%S)T\n" ⌛
printf "%(%Y-%m-%d %H:%M:%S)T is %s\n" -1 "the time" ⌛
```

## **02\_10 Working with arrays**

Let's enter the realm of arrays and unleash the power of list manipulation! 📚🔀

```bash
declare -a snacks=("apple" "banana" "orange")
echo ${snacks[2]} 🍎🍌🍊
snacks[5]="grapes"
snacks+=("mango")
echo ${snacks[@]} 🍇🥭🍎🍌🍊
for i in {0..6}; do echo "$i: ${snacks[$i]}"; done 📋
declare -A office
office[city]="San Francisco"
office["building name"]="HQ West"
echo ${office["building name"]} is in ${office[city]}" 🌆
```

## **03\_01 Conditional statements with the 'if' keyword**

Get ready for some conditional fun! Let's make decisions in our scripts! 🤔✅❌

```bash
#!/bin/bash
declare -i a=3
if [[ $a -gt 4 ]]; then
    echo "$a is greater than 4!"
else
    echo "$a is not greater than 4!"
fi
```

```bash
#!/bin/bash
declare -i a=3
if [[ $a -gt 4 ]]; then
    echo "$a is greater than 4!"
elif (( $a > 2 )); then
    echo "$a is greater than 2."
else
    echo "$a is not greater than 4!"
fi
```

## **03\_02 Working with while and until loops**

Time to create loops and keep things interesting! Let's repeat some actions! 🔁🔄

```bash
#!/bin/bash
echo "While Loop"
declare -i n=0
while (( n < 10 ))
do
    echo "n:$n"
    (( n++ ))
done
echo -e "\nUntil Loop"
declare -i m=0
until (( m == 10 )); do
    echo "m:$m"
    (( m++ ))
done
```

```bash
#!/bin/bash
echo "While Loop"
declare -i n=0
while (( n < 10 ))
do
    echo "n:$n"
    (( n++ ))
done
echo -e "\nUntil Loop"
declare -i m=0
until ((m > m)); do
    echo "m:$m"
    (( m++ ))
done
```

## **03\_03 Introducing 'for' loops**

Let's dive into the world of 'for' loops! Prepare for repetitive awesomeness! 🔄🔁

```bash
#!/bin/bash
for i in 1 2 3
do
    echo $i
done
for i in 1 2 3; do echo $i; done
```

```bash
#!/bin/bash
for i in {1..100}
do
    echo $i
done
```

```bash
#!/bin/bash
for (( i=1; i<=100; i++ ))
do
    echo $i
done
```

```bash
#!/bin/bash
declare -a fruits=("apple" "banana" "cherry")
for i in ${fruits[@]}
do
    echo $i
done
```

```bash
#!/bin/bash
declare -A arr
arr["name"]="scott"
arr["id"]="1234"
for i in "${!arr[@]}"
do
    echo $i: "${arr[$i]}"
done
```

```bash
#!/bin/bash
for i in $(ls)
do
    echo "Found a file: $i"
done
```

```bash
#!/bin/bash
for i in *
do
    echo "Found a file: $i"
done
```

## **03\_04 Selecting behavior using 'case'**

Let's have some fun with the 'case' statement! It's like a menu for our script! 📝👈

```bash
#!/bin/bash
animal="dog"
case $animal in
    bird) echo "Avian";;
    dog|puppy) echo "Canine";;
    *) echo "No match!";;
esac
```

## **03\_05 Using functions**

Get ready to define and use functions in our script! Let's make our code modular! 🧩🔧

```bash
#!/bin/bash
greet() {
    echo "Hi there."
}
echo "And now, a greeting..."
greet
```

```bash
#!/bin/bash
greet() {
    echo "Hi there, $1"
}
echo "And now, a greeting..."
greet Scott
```

```bash
#!/bin/bash
greet() {
    echo "Hi there, $1. What a nice $2"
}
echo "And now, a greeting..."
greet Scott Morning
greet Everybody Evening
```

```bash
#!/bin/bash
numberthing() {
    declare -i i=1
    for f in $@; do
        echo "$i: $f"
        (( i += 1 ))
    done
    echo "This counting was brought to you by $FUNCNAME."
}
numberthing "$(ls /)"
echo
numberthing pine birch maple spruce
```

```bash
#!/bin/bash
var1="I'm variable 1"
myfunction() {
    var2="I'm variable 2"
    local var3="I'm variable 3"
}
myfunction
echo $var1 📦
echo $var2 📦
echo $var3 📦
```

## **03\_06 Reading and writing text files**

Let's read and write text files like wordsmiths! Prepare for textual adventures! 📜🖊️

```bash
#!/bin/bash
for i in 1 2 3 4 5
do
    echo "This is line $i" > ~/textfile.txt
done
```

```bash
#!/bin/bash
for i in 1 2 3 4 5
do
    echo "This is line $i" >> ~/textfile.txt
done
```

```bash
#!/bin/bash
while read f
do 
    echo "I read a line and it says: $f"
done < ~/textfile.txt
```

## **04\_01 Working with arguments**

Let's dive into the world of command-line arguments! Prepare for some interactive script action! 📥📤

```bash
#!/bin/bash
echo "The $0 script got the argument $1" 🎯
```

```bash
#!/bin/bash
echo "The $0 script got the argument $1" 🎯
echo "Argument 2 is $2" 🎯
```

```bash
#!/bin/bash
for i in $@
do
    echo $i
done
```

```bash
#!/bin/bash
for i in $@
do
    echo $i
done
echo "There were $# arguments." 🧮
```

## **04\_02 Working with options**

Time to level up with command-line options! Let's make our scripts more versatile! ⚙️🔀

```bash
#!/bin/bash
while getopts u:p: option; do
    case $option in
        u) user=$OPTARG;;
        p) pass=$OPTARG;;
    esac
done
echo "user: $user / pass: $pass" 🤫
```

```bash
#!/bin/bash
while getopts u:p:ab option; do
    case $option in
        u) user=$OPTARG;;
        p) pass=$OPTARG;;
        a) echo "got the A flag" 🚩;;
        b) echo "got the B flag" 🚩;;
    esac
done
echo "user: $user / pass: $pass" 🤫
```

```bash
#!/bin/bash
while getopts :u:p:ab option; do
    case $option in
        u) user=$OPTARG;;
        p) pass=$OPTARG;;
        a) echo "got the A flag" 🚩;;
        b) echo "got the B flag" 🚩;;
        \?) echo "Unknown option: -$OPTARG" ❓;;
    esac
done
echo "user: $user / pass: $pass" 🤫
```

## **04\_03 Interactive scripts**

Get ready for interactive script magic! Let's make our scripts communicate with users! 💬✨

```bash
#!/bin/bash
echo "What is your name?"
read name
echo "Nice to meet you, $name" 👋
```

```bash
#!/bin/bash
echo "What is your favorite color?"
read -r color
echo "Ah, $color, an excellent choice!" 🎨
```

```bash
#!/bin/bash
read -p "What is your favorite animal? " animal
echo "Ah, the $animal, a magnificent creature!" 🦁
```

```bash
#!/bin/bash
read -p "What is your favorite color? " -n 1 -t 5 color
echo -e "\nAh, $color, an excellent choice!" 🎨
```

## **04\_04 Getting input from users**

Time to get creative with user input! Let's validate and process the information! 🕵️‍♂️💡

```bash
#!/bin/bash
read -p "What is your age? " age
if [[ $age =~ ^[0-9]+$ ]]; then
    echo "Your age is $age" 🎂
else
    echo "Invalid age entered!" ❌
fi
```

```bash
#!/bin/bash
read -p "Enter a file or directory: " path
if [[ -e $path ]]; then
    echo "$path exists!" 🗂️
else
    echo "$path does not exist!" ❌
fi
```

```bash
#!/bin/bash
while read -p "Enter a number: " number; do
    if [[ $number =~ ^[0-9]+$ ]]; then
        echo "Valid number entered: $number" 🧮
        break
    else
        echo "Invalid number entered!" ❌
    fi
done
```

```bash
#!/bin/bash
while read -p "Enter a name: " name; do
    if [[ -z $name ]]; then
        echo "Name cannot be empty!" ❌
    else
        echo "Hello, $name!" 👋
        break
    fi
done
```

## **04\_05 Exiting the script**

It's time to wrap things up! Let's gracefully exit our scripts and say our goodbyes! 👋🚀

```bash
#!/bin/bash
echo "Hello, world!" 👋
exit 0
```

```bash
#!/bin/bash
echo "Hello, world!" 👋
exit 1
```

```bash
#!/bin/bash
echo "Hello, world!" 👋
exit
```

```bash
#!/bin/bash
echo "Hello, world!" 👋
return 0
```

```bash
#!/bin/bash
function exit_script {
    echo "Exiting..."
    exit
}
echo "Hello, world!" 👋
exit_script
echo "This line will not be executed."
```

## **Conclusion:**

Congratulations on completing this fun-filled bash scripting adventure! 🎉🎉 We hope you had a great time exploring the wacky and powerful world of the command line. Remember, the possibilities with bash scripting are endless, so keep experimenting and creating! Happy scripting! 😄💻

Hope you like my blog...!

if you like the content follow me on LinkedIn: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)

Follow my Whatsapp & telegram community: [https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3](https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3)

[https://t.me/ExplorewithAshok](https://t.me/ExplorewithAshok)

Happy learning......!