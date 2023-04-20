 LeonSheff  ~  mkdir students mentors; touch students/students_list.txt mentors/mentors_list.txt
 LeonSheff  ~  vim students/students_list.txt
 LeonSheff  ~  # Изменения в mentors/mentors_list.txt внес через вторую вкладку vim
 LeonSheff  ~  tree -L 2
.
├── Downloads
├── main
│   ├── env
│   ├── newfile.txt
│   ├── new.py
│   └── sqrt_example.py
├── mentors
│   └── mentors_list.txt
└── students
    └── students_list.txt

5 directories, 5 files
 LeonSheff  ~  mv mentors/mentors_list.txt students/
 LeonSheff  ~  tree -L 2
.
├── Downloads
├── main
│   ├── env
│   ├── newfile.txt
│   ├── new.py
│   └── sqrt_example.py
├── mentors
└── students
    ├── mentors_list.txt
    └── students_list.txt

5 directories, 5 files
 LeonSheff  ~  rm -r mentors/
 LeonSheff  ~  mv students/ students_and_mentors/
 LeonSheff  ~  tree -L 2
.
├── Downloads
├── main
│   ├── env
│   ├── newfile.txt
│   ├── new.py
│   └── sqrt_example.py
└── students_and_mentors
    ├── mentors_list.txt
    └── students_list.txt

4 directories, 5 files
 LeonSheff  ~  rm -r students_and_mentors/
 LeonSheff  ~  tree -L 2
.
├── Downloads
└── main
    ├── env
    ├── newfile.txt
    ├── new.py
    └── sqrt_example.py

3 directories, 3 files
Доп. задания:

 LeonSheff  ~  tree -L 2
.
├── Downloads
└── main
    ├── env
    ├── newfile.txt
    ├── new.py
    └── sqrt_example.py

3 directories, 3 files
 LeonSheff  ~  vim file1
 LeonSheff  ~  cp file1 file2
 LeonSheff  ~  ln -s file1 file3
 LeonSheff  ~  ln file1 file4
total 20
46409 drwxr-xr-x 2 Leon 4096 мар 26 21:43 Downloads
39595 -rw-r--r-- 2 Leon   24 апр  1 23:15 file1
40061 -rw-r--r-- 1 Leon   24 апр  1 23:16 file2
50595 lrwxrwxrwx 1 Leon    5 апр  1 23:16 file3 -> file1
39595 -rw-r--r-- 2 Leon   24 апр  1 23:15 file4
 1819 drwxr-xr-x 3 Leon 4096 мар 31 16:56 main
 LeonSheff  ~  rm file1
 LeonSheff  ~  ls -li
total 16
46409 drwxr-xr-x 2 Leon 4096 мар 26 21:43 Downloads
40061 -rw-r--r-- 1 Leon   24 апр  1 23:16 file2
50595 lrwxrwxrwx 1 Leon    5 апр  1 23:16 file3 -> file1
39595 -rw-r--r-- 1 Leon   24 апр  1 23:15 file4
 1819 drwxr-xr-x 3 Leon 4096 мар 31 16:56 main
 LeonSheff  ~  cat file*
some comtent in file...
cat: file3: No such file or directory
some comtent in file...
 ✘  LeonSheff  ~  # был вывод содержимого из 2, 3 и 4 файлов по порядку
 ✘  LeonSheff  ~  mv file2 text2
 LeonShef  ~  mv file3 test
 LeonShef  ~  mv file4 text4
 LeonShef  ~  ls -li
total 16
46409 drwxr-xr-x 2 Leon 4096 мар 26 21:43 Downloads
 1819 drwxr-xr-x 3 Leon 4096 мар 31 16:56 main
50595 lrwxrwxrwx 1 Leon    5 апр  1 23:16 test -> file1
40061 -rw-r--r-- 1 Leon   24 апр  1 23:16 text2
39595 -rw-r--r-- 1 Leon   24 апр  1 23:15 text4
 LeonSheff  ~  mv text? main/; mv test main/
 LeonSheff  ~  tree -L 2
.
├── Downloads
└── main
    ├── env
    ├── newfile.txt
    ├── new.py
    ├── sqrt_example.py
    ├── test -> file1
    ├── text2
    └── text4

3 directories, 6 files