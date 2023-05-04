LeonSheff  main  vi file1
 LeonSheff  main  ./file1
Задание 1
LeonS
LeonS
LeonS
Задание 2
0 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30 32 34 36 38 40 42 44 46 48 50 52 54 56 58 60 62 64 66 68 70 72 74 76 78 80 82 84 86 88 90 92 94 96 98 100
Задание 3
-rw-r--r--
-rwxr-xr-x
total 8

 LeonSheff  main  cat file1
#!/bin/bash

echo Задание 1

for rep in {1..3}
do
  echo $(whoami)
done

echo Задание 2

n=0
while [ $n -le 100 ]
do
  if [ $(expr $n % 2) == 0 ]
    then
      echo -n "$n "
  fi
  (( n++ ))
done

echo -e "\nЗадание 3"

ls -l | cut -c1-10 | sort | uniq

echo;
 LeonSheff  main  
 LeonSheff  main  
 LeonSheff  main  
 LeonSheff  main  vi task4
 LeonSheff  main  chmod +x task4
 LeonSheff  main  tree .
.
├── Dockerfile
├── file1
├── file2
├── task4
├── test.txt
└── test.txt.bak

0 directories, 6 files
 LeonSheff  main  ./task4 .
All temp and backup files cleared!
 LeonSheff  main  tree .
.
├── Dockerfile
├── file1
├── file2
├── task4
└── test.txt

0 directories, 5 files
 LeonSheff  main  ./task4 /home/LeonS/test
Err: No such directory.
 LeonSheff  main  cat task4
#!/bin/bash

dir=$1
if [ -e $dir ]; then
  find $dir -type f \( -name "*.bak" -o -name "*.tmp" -o -name "*.backup" \) -delete
        echo "All temp and backup files cleared!"
elif [ -z $dir ]; then
  echo "The string is empty."
  exit
else
 echo "Err: No such directory."
fi
 LeonSheff  main 