# CSE 15L Lab 3 Report
## By Parth Paliwal

`Part 1`
---
A failure-inducing input for the buggy program, as a JUnit test and any associated code (write it as a code block in Markdown)

```
public void testReverseInPlace() {
  int[] input1 = { 1,2,3,4 };
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{ 4,3,2,1 }, input1);
}
```
An input that doesn't induce a failure, as a JUnit test and any associated code (write it as a code block in Markdown)
```
public void testReverseInPlace() {
  int[] input1 = { 0,0,0 };
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{ 0,0,0 }, input1);
}
```
The symptom, as the output of running the tests (provide it as a screenshot of running JUnit with at least the two inputs above)

Here's the output of the test with the failure inducing input
![Image](screenshots/FailureLab3.png)

Here's the output of the test with the non-failure inducing input
![Image](screenshots/SuccessLab3.png)

The bug, as the before-and-after code change required to fix it (as two code blocks in Markdown)

Buggy code:
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
    arr[i] = newArray[arr.length - i - 1];
  }
  return arr;
}
```

Revised code:
```
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    newArray[i] = arr[arr.length - i - 1];
  }
  return newArray;
}
```

The reason the old code was faulty was because instead of assigning the original arrays values to the reversed array, it was assigning the values the other way around. This meant that the new array with default values of 0, were getting returned thus the code didnt work. It worked however if all the values in the original array were 0 because in that case the new array and the original array had the same values.

`Part 2`
---
## Option 2: Find (finds files and directories)

### Example 1: ```find ./technical/911report -type f```
Lists out all the files in the directory
Output:
```
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-13.5.txt
./technical/911report/chapter-13.1.txt
./technical/911report/chapter-13.2.txt
./technical/911report/chapter-13.3.txt
./technical/911report/chapter-3.txt
./technical/911report/chapter-2.txt
./technical/911report/chapter-1.txt
./technical/911report/chapter-5.txt
./technical/911report/chapter-6.txt
./technical/911report/chapter-7.txt
./technical/911report/chapter-9.txt
./technical/911report/chapter-8.txt
./technical/911report/preface.txt
./technical/911report/chapter-12.txt
./technical/911report/chapter-10.txt
./technical/911report/chapter-11.txt
```

### Example 2: ```find ./technical/911report -type d```
Lists all the directories

Output:
```
./technical/911report
```

### Example 3: ```find ./technical/911report -type f -name "chapter1.txt"```
searches for a file named chapter1.txt within the ./technical/911report directory and its subdirectories.

There is no output

### Example 4: ```find ./technical -type d -name "dir1"```
searches for a directory named dir1 within the ./technical directory and its subdirectories.

There is no output

### Example 5: ```find ./technical -type f -mtime -5```
Lists all the directories

Output:
```
./technical/.DS_Store
```
searches for files modified within the last 5 days within the ./technical directory and its subdirectories.

### Example 6: ```find ./technical -type d -mtime -30```
searches for directories modified within the last 30 days within the ./technical directory and its subdirectories.

Output:
```
./technical
./technical/government
./technical/government/About_LSC
./technical/government/Env_Prot_Agen
./technical/government/Alcohol_Problems
./technical/government/Gen_Account_Office
./technical/government/Post_Rate_Comm
./technical/government/Media
./technical/plos
./technical/biomed
./technical/911report
```

### Example 7: ```find ./technical -type f -exec ls -l {} \;```
executes the ls -l command on each file found within the ./technical directory and its subdirectories.

Output:
```
-rwxr-xr-x  1 parthpaliwal  staff  27074 Feb  7 12:02 ./technical/biomed/gb-2001-2-6-research0020.txt
-rwxr-xr-x  1 parthpaliwal  staff  40558 Feb  7 12:02 ./technical/biomed/1472-6785-2-7.txt
-rwxr-xr-x  1 parthpaliwal  staff  27490 Feb  7 12:02 ./technical/biomed/1471-2180-1-16.txt
-rwxr-xr-x  1 parthpaliwal  staff  27848 Feb  7 12:02 ./technical/biomed/ar745.txt
-rwxr-xr-x  1 parthpaliwal  staff  34258 Feb  7 12:02 ./technical/biomed/1472-6890-3-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  30360 Feb  7 12:02 ./technical/biomed/cc103.txt
-rwxr-xr-x  1 parthpaliwal  staff  32894 Feb  7 12:02 ./technical/biomed/1471-2202-2-16.txt
-rwxr-xr-x  1 parthpaliwal  staff  25237 Feb  7 12:02 ./technical/biomed/ar792.txt
-rwxr-xr-x  1 parthpaliwal  staff  88698 Feb  7 12:02 ./technical/biomed/gb-2002-3-12-research0083.txt
-rwxr-xr-x  1 parthpaliwal  staff  31355 Feb  7 12:02 ./technical/biomed/1471-2180-3-13.txt
-rwxr-xr-x  1 parthpaliwal  staff  25317 Feb  7 12:02 ./technical/biomed/1471-2210-2-8.txt
-rwxr-xr-x  1 parthpaliwal  staff  42284 Feb  7 12:02 ./technical/biomed/1472-6793-1-8.txt
-rwxr-xr-x  1 parthpaliwal  staff  29911 Feb  7 12:02 ./technical/biomed/1471-2458-2-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  31607 Feb  7 12:02 ./technical/biomed/1472-6750-2-21.txt
-rwxr-xr-x  1 parthpaliwal  staff  34936 Feb  7 12:02 ./technical/biomed/1471-2431-3-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  21093 Feb  7 12:02 ./technical/biomed/1472-6882-2-10.txt
-rwxr-xr-x  1 parthpaliwal  staff  48211 Feb  7 12:02 ./technical/biomed/1471-2350-3-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  44323 Feb  7 12:02 ./technical/biomed/gb-2002-3-11-research0062.txt
-rwxr-xr-x  1 parthpaliwal  staff  15301 Feb  7 12:02 ./technical/biomed/1472-6882-2-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  27931 Feb  7 12:02 ./technical/biomed/gb-2002-3-11-research0060.txt
-rwxr-xr-x  1 parthpaliwal  staff  34190 Feb  7 12:02 ./technical/biomed/1471-213X-3-7.txt
-rwxr-xr-x  1 parthpaliwal  staff  32569 Feb  7 12:02 ./technical/biomed/cc303.txt
-rwxr-xr-x  1 parthpaliwal  staff  22286 Feb  7 12:02 ./technical/biomed/cc1477.txt
-rwxr-xr-x  1 parthpaliwal  staff  24515 Feb  7 12:02 ./technical/biomed/1471-2407-3-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  50740 Feb  7 12:02 ./technical/biomed/1471-2377-3-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  37919 Feb  7 12:02 ./technical/biomed/1471-2180-3-11.txt
-rwxr-xr-x  1 parthpaliwal  staff  41121 Feb  7 12:02 ./technical/biomed/gb-2002-3-12-research0081.txt
-rwxr-xr-x  1 parthpaliwal  staff  31319 Feb  7 12:02 ./technical/biomed/cc1852.txt
-rwxr-xr-x  1 parthpaliwal  staff  20338 Feb  7 12:02 ./technical/biomed/1471-2164-4-25.txt
-rwxr-xr-x  1 parthpaliwal  staff  40379 Feb  7 12:02 ./technical/biomed/1471-2091-3-22.txt
-rwxr-xr-x  1 parthpaliwal  staff  23188 Feb  7 12:02 ./technical/biomed/1471-2202-2-14.txt
-rwxr-xr-x  1 parthpaliwal  staff  18841 Feb  7 12:02 ./technical/biomed/1471-2164-3-10.txt
-rwxr-xr-x  1 parthpaliwal  staff  31181 Feb  7 12:02 ./technical/biomed/1471-2164-4-19.txt
-rwxr-xr-x  1 parthpaliwal  staff  12557 Feb  7 12:02 ./technical/biomed/cc713.txt
-rwxr-xr-x  1 parthpaliwal  staff  41490 Feb  7 12:02 ./technical/biomed/1471-2172-3-16.txt
-rwxr-xr-x  1 parthpaliwal  staff  26000 Feb  7 12:02 ./technical/biomed/1471-2180-1-28.txt
-rwxr-xr-x  1 parthpaliwal  staff  25804 Feb  7 12:02 ./technical/biomed/1471-230X-1-10.txt
-rwxr-xr-x  1 parthpaliwal  staff  26337 Feb  7 12:02 ./technical/biomed/1471-2121-2-22.txt
-rwxr-xr-x  1 parthpaliwal  staff  25529 Feb  7 12:02 ./technical/biomed/1471-2334-2-29.txt
-rwxr-xr-x  1 parthpaliwal  staff  25531 Feb  7 12:02 ./technical/biomed/1471-2121-3-8.txt
-rwxr-xr-x  1 parthpaliwal  staff  27938 Feb  7 12:02 ./technical/biomed/1472-6963-1-8.txt
-rwxr-xr-x  1 parthpaliwal  staff  23589 Feb  7 12:02 ./technical/biomed/1471-2296-3-19.txt
-rwxr-xr-x  1 parthpaliwal  staff  28027 Feb  7 12:02 ./technical/biomed/1471-2407-2-15.txt
-rwxr-xr-x  1 parthpaliwal  staff  47239 Feb  7 12:02 ./technical/biomed/1471-2105-3-17.txt
-rwxr-xr-x  1 parthpaliwal  staff  21061 Feb  7 12:02 ./technical/biomed/1471-230X-3-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  17933 Feb  7 12:02 ./technical/biomed/ar430.txt
-rwxr-xr-x  1 parthpaliwal  staff  46131 Feb  7 12:02 ./technical/biomed/1471-2156-3-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  20589 Feb  7 12:02 ./technical/biomed/1471-2466-2-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  31087 Feb  7 12:02 ./technical/biomed/1471-2296-3-18.txt
-rwxr-xr-x  1 parthpaliwal  staff  37446 Feb  7 12:02 ./technical/biomed/1471-2105-3-16.txt
-rwxr-xr-x  1 parthpaliwal  staff  32906 Feb  7 12:02 ./technical/biomed/1472-6920-2-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  29768 Feb  7 12:02 ./technical/biomed/1476-072X-2-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  27689 Feb  7 12:02 ./technical/biomed/gb-2003-4-9-r60.txt
-rwxr-xr-x  1 parthpaliwal  staff  38211 Feb  7 12:02 ./technical/biomed/ar140.txt
-rwxr-xr-x  1 parthpaliwal  staff  52824 Feb  7 12:02 ./technical/biomed/gb-2003-4-3-r17.txt
-rwxr-xr-x  1 parthpaliwal  staff  37722 Feb  7 12:02 ./technical/biomed/1472-6793-2-11.txt
-rwxr-xr-x  1 parthpaliwal  staff  19040 Feb  7 12:02 ./technical/biomed/1472-6823-2-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  30845 Feb  7 12:02 ./technical/biomed/1471-2180-1-29.txt
-rwxr-xr-x  1 parthpaliwal  staff  46108 Feb  7 12:02 ./technical/biomed/1471-2172-2-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  21314 Feb  7 12:02 ./technical/biomed/1471-2407-1-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  25298 Feb  7 12:02 ./technical/biomed/1471-2091-2-9.txt
-rwxr-xr-x  1 parthpaliwal  staff  28119 Feb  7 12:02 ./technical/biomed/1471-2202-2-15.txt
-rwxr-xr-x  1 parthpaliwal  staff  33815 Feb  7 12:02 ./technical/biomed/1471-2091-3-23.txt
-rwxr-xr-x  1 parthpaliwal  staff  26222 Feb  7 12:02 ./technical/biomed/1471-2164-4-24.txt
-rwxr-xr-x  1 parthpaliwal  staff  18068 Feb  7 12:02 ./technical/biomed/1471-213X-1-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  28874 Feb  7 12:02 ./technical/biomed/gb-2002-3-12-research0080.txt
-rwxr-xr-x  1 parthpaliwal  staff  30027 Feb  7 12:02 ./technical/biomed/1471-2180-3-10.txt
-rwxr-xr-x  1 parthpaliwal  staff  26600 Feb  7 12:02 ./technical/biomed/cc1476.txt
-rwxr-xr-x  1 parthpaliwal  staff  25661 Feb  7 12:02 ./technical/biomed/1471-2407-3-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  22131 Feb  7 12:02 ./technical/biomed/1471-2431-3-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  25685 Feb  7 12:02 ./technical/biomed/bcr294.txt
-rwxr-xr-x  1 parthpaliwal  staff  26586 Feb  7 12:02 ./technical/biomed/gb-2002-3-11-research0061.txt
-rwxr-xr-x  1 parthpaliwal  staff  39369 Feb  7 12:02 ./technical/biomed/1477-7827-1-43.txt
-rwxr-xr-x  1 parthpaliwal  staff  25725 Feb  7 12:02 ./technical/biomed/1475-2832-1-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  30440 Feb  7 12:02 ./technical/biomed/1471-2199-3-12.txt
-rwxr-xr-x  1 parthpaliwal  staff  20783 Feb  7 12:02 ./technical/biomed/1471-2202-1-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  19066 Feb  7 12:02 ./technical/biomed/1472-6750-2-13.txt
-rwxr-xr-x  1 parthpaliwal  staff  20745 Feb  7 12:02 ./technical/biomed/cc2172.txt
-rwxr-xr-x  1 parthpaliwal  staff  19300 Feb  7 12:02 ./technical/biomed/1472-6793-1-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  35907 Feb  7 12:02 ./technical/biomed/1471-2210-2-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  37729 Feb  7 12:02 ./technical/biomed/1471-213X-1-9.txt
-rwxr-xr-x  1 parthpaliwal  staff  20958 Feb  7 12:02 ./technical/biomed/1471-2164-3-34.txt
-rwxr-xr-x  1 parthpaliwal  staff  26254 Feb  7 12:02 ./technical/biomed/1471-2164-4-15.txt
-rwxr-xr-x  1 parthpaliwal  staff  35079 Feb  7 12:02 ./technical/biomed/1471-2202-3-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  20061 Feb  7 12:02 ./technical/biomed/1471-2202-2-18.txt
-rwxr-xr-x  1 parthpaliwal  staff  18512 Feb  7 12:02 ./technical/biomed/cc2358.txt
-rwxr-xr-x  1 parthpaliwal  staff  26409 Feb  7 12:02 ./technical/biomed/1472-6793-3-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  56348 Feb  7 12:02 ./technical/biomed/gb-2002-3-12-research0072.txt
-rwxr-xr-x  1 parthpaliwal  staff  16645 Feb  7 12:02 ./technical/biomed/1472-6963-3-11.txt
-rwxr-xr-x  1 parthpaliwal  staff  27276 Feb  7 12:02 ./technical/biomed/1472-6963-3-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  15618 Feb  7 12:02 ./technical/biomed/1476-4598-2-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  20506 Feb  7 12:02 ./technical/biomed/1477-7827-1-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  62700 Feb  7 12:02 ./technical/biomed/1475-4924-1-10.txt
-rwxr-xr-x  1 parthpaliwal  staff  27708 Feb  7 12:02 ./technical/biomed/1472-6874-2-13.txt
-rwxr-xr-x  1 parthpaliwal  staff  18617 Feb  7 12:02 ./technical/biomed/1471-2369-4-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  48187 Feb  7 12:02 ./technical/biomed/1471-2121-3-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  26002 Feb  7 12:02 ./technical/biomed/1471-2121-2-12.txt
-rwxr-xr-x  1 parthpaliwal  staff  24898 Feb  7 12:02 ./technical/biomed/1471-2148-2-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  39964 Feb  7 12:02 ./technical/biomed/1475-925X-2-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  29403 Feb  7 12:02 ./technical/biomed/1471-2148-1-14.txt
-rwxr-xr-x  1 parthpaliwal  staff  29550 Feb  7 12:02 ./technical/biomed/1471-2407-2-19.txt
-rwxr-xr-x  1 parthpaliwal  staff  35701 Feb  7 12:02 ./technical/biomed/1471-2210-2-14.txt
-rwxr-xr-x  1 parthpaliwal  staff  36377 Feb  7 12:02 ./technical/biomed/1475-2867-3-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  18681 Feb  7 12:02 ./technical/biomed/ar429.txt
-rwxr-xr-x  1 parthpaliwal  staff  19545 Feb  7 12:02 ./technical/biomed/1471-2407-2-31.txt
-rwxr-xr-x  1 parthpaliwal  staff  31764 Feb  7 12:02 ./technical/biomed/1471-2105-3-26.txt
-rwxr-xr-x  1 parthpaliwal  staff  17188 Feb  7 12:02 ./technical/biomed/1477-7525-1-12.txt
-rwxr-xr-x  1 parthpaliwal  staff  26749 Feb  7 12:02 ./technical/biomed/1471-2407-2-18.txt
-rwxr-xr-x  1 parthpaliwal  staff  37814 Feb  7 12:02 ./technical/biomed/1471-2105-4-13.txt
-rwxr-xr-x  1 parthpaliwal  staff  46030 Feb  7 12:02 ./technical/biomed/gb-2003-4-1-r5.txt
-rwxr-xr-x  1 parthpaliwal  staff  32166 Feb  7 12:02 ./technical/biomed/1471-2334-2-24.txt
-rwxr-xr-x  1 parthpaliwal  staff  33364 Feb  7 12:02 ./technical/biomed/1471-2318-3-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  36043 Feb  7 12:02 ./technical/biomed/1471-2156-2-12.txt
-rwxr-xr-x  1 parthpaliwal  staff  29292 Feb  7 12:02 ./technical/biomed/1471-2180-1-31.txt
-rwxr-xr-x  1 parthpaliwal  staff  15818 Feb  7 12:02 ./technical/biomed/1476-4598-2-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  24653 Feb  7 12:02 ./technical/biomed/1472-684X-2-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  12826 Feb  7 12:02 ./technical/biomed/1471-5945-3-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  37540 Feb  7 12:02 ./technical/biomed/1472-6963-3-7.txt
-rwxr-xr-x  1 parthpaliwal  staff  27864 Feb  7 12:02 ./technical/biomed/1475-2891-2-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  45414 Feb  7 12:02 ./technical/biomed/1471-2091-2-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  27647 Feb  7 12:02 ./technical/biomed/1472-6793-3-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  29681 Feb  7 12:02 ./technical/biomed/1475-4924-1-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  32908 Feb  7 12:02 ./technical/biomed/1471-2202-2-19.txt
-rwxr-xr-x  1 parthpaliwal  staff  29139 Feb  7 12:02 ./technical/biomed/1471-2091-3-13.txt
-rwxr-xr-x  1 parthpaliwal  staff  18940 Feb  7 12:02 ./technical/biomed/1471-2164-4-14.txt
-rwxr-xr-x  1 parthpaliwal  staff  36670 Feb  7 12:02 ./technical/biomed/1471-2164-3-35.txt
-rwxr-xr-x  1 parthpaliwal  staff  33886 Feb  7 12:02 ./technical/biomed/1471-2164-4-28.txt
-rwxr-xr-x  1 parthpaliwal  staff  33687 Feb  7 12:02 ./technical/biomed/cc2167.txt
-rwxr-xr-x  1 parthpaliwal  staff  43955 Feb  7 12:02 ./technical/biomed/bcr273.txt
-rwxr-xr-x  1 parthpaliwal  staff  40046 Feb  7 12:02 ./technical/biomed/1477-7827-1-54.txt
-rwxr-xr-x  1 parthpaliwal  staff  21319 Feb  7 12:02 ./technical/biomed/1471-2334-2-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  25396 Feb  7 12:02 ./technical/biomed/1471-2199-3-11.txt
-rwxr-xr-x  1 parthpaliwal  staff  21912 Feb  7 12:02 ./technical/biomed/1472-6750-2-10.txt
-rwxr-xr-x  1 parthpaliwal  staff  33152 Feb  7 12:02 ./technical/biomed/1471-2210-2-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  29402 Feb  7 12:02 ./technical/biomed/cc2171.txt
-rwxr-xr-x  1 parthpaliwal  staff  20694 Feb  7 12:02 ./technical/biomed/1471-2164-3-23.txt
-rwxr-xr-x  1 parthpaliwal  staff  33581 Feb  7 12:02 ./technical/biomed/1471-2164-4-16.txt
-rwxr-xr-x  1 parthpaliwal  staff  24602 Feb  7 12:02 ./technical/biomed/ar774.txt
-rwxr-xr-x  1 parthpaliwal  staff  83194 Feb  7 12:02 ./technical/biomed/1476-511X-1-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  25064 Feb  7 12:02 ./technical/biomed/1472-6963-3-12.txt
-rwxr-xr-x  1 parthpaliwal  staff  25458 Feb  7 12:02 ./technical/biomed/1471-2091-2-7.txt
-rwxr-xr-x  1 parthpaliwal  staff  57162 Feb  7 12:02 ./technical/biomed/gb-2002-3-12-research0071.txt
-rwxr-xr-x  1 parthpaliwal  staff  30646 Feb  7 12:02 ./technical/biomed/1471-2180-1-33.txt
-rwxr-xr-x  1 parthpaliwal  staff  24629 Feb  7 12:02 ./technical/biomed/gb-2000-1-1-research002.txt
-rwxr-xr-x  1 parthpaliwal  staff  28714 Feb  7 12:02 ./technical/biomed/gb-2001-3-1-research0005.txt
-rwxr-xr-x  1 parthpaliwal  staff  44544 Feb  7 12:02 ./technical/biomed/bcr45.txt
-rwxr-xr-x  1 parthpaliwal  staff  30279 Feb  7 12:02 ./technical/biomed/1471-2091-4-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  29546 Feb  7 12:02 ./technical/biomed/gb-2003-4-1-r7.txt
-rwxr-xr-x  1 parthpaliwal  staff  27094 Feb  7 12:02 ./technical/biomed/1471-2334-2-26.txt
-rwxr-xr-x  1 parthpaliwal  staff  42311 Feb  7 12:02 ./technical/biomed/1471-2121-2-11.txt
-rwxr-xr-x  1 parthpaliwal  staff  22954 Feb  7 12:02 ./technical/biomed/1471-5945-1-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  78562 Feb  7 12:02 ./technical/biomed/1471-2105-3-18.txt
-rwxr-xr-x  1 parthpaliwal  staff  28796 Feb  7 12:02 ./technical/biomed/1471-2261-3-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  12110 Feb  7 12:02 ./technical/biomed/1471-2105-3-24.txt
-rwxr-xr-x  1 parthpaliwal  staff  19791 Feb  7 12:02 ./technical/biomed/1476-5918-1-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  21781 Feb  7 12:02 ./technical/biomed/1477-7525-1-10.txt
-rwxr-xr-x  1 parthpaliwal  staff  31838 Feb  7 12:02 ./technical/biomed/gb-2002-3-5-research0024.txt
-rwxr-xr-x  1 parthpaliwal  staff  43797 Feb  7 12:02 ./technical/biomed/1471-2105-3-30.txt
-rwxr-xr-x  1 parthpaliwal  staff  31098 Feb  7 12:02 ./technical/biomed/1471-2407-2-33.txt
-rwxr-xr-x  1 parthpaliwal  staff  49968 Feb  7 12:02 ./technical/biomed/gb-2002-3-5-research0025.txt
-rwxr-xr-x  1 parthpaliwal  staff  43855 Feb  7 12:02 ./technical/biomed/1471-2261-3-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  41339 Feb  7 12:02 ./technical/biomed/1471-2199-3-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  51543 Feb  7 12:02 ./technical/biomed/1471-2121-2-10.txt
-rwxr-xr-x  1 parthpaliwal  staff  39935 Feb  7 12:02 ./technical/biomed/1471-2121-3-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  35377 Feb  7 12:02 ./technical/biomed/1471-2334-2-27.txt
-rwxr-xr-x  1 parthpaliwal  staff  26047 Feb  7 12:02 ./technical/biomed/gb-2001-3-1-research0004.txt
-rwxr-xr-x  1 parthpaliwal  staff  34261 Feb  7 12:02 ./technical/biomed/1471-2105-2-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  19386 Feb  7 12:02 ./technical/biomed/1471-2261-1-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  18620 Feb  7 12:02 ./technical/biomed/gb-2003-4-3-r18.txt
-rwxr-xr-x  1 parthpaliwal  staff  34084 Feb  7 12:02 ./technical/biomed/ar615.txt
-rwxr-xr-x  1 parthpaliwal  staff  18964 Feb  7 12:02 ./technical/biomed/ar601.txt
-rwxr-xr-x  1 parthpaliwal  staff  24279 Feb  7 12:02 ./technical/biomed/1476-4598-2-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  29525 Feb  7 12:02 ./technical/biomed/1472-684X-2-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  47026 Feb  7 12:02 ./technical/biomed/1471-2180-1-26.txt
-rwxr-xr-x  1 parthpaliwal  staff  27043 Feb  7 12:02 ./technical/biomed/1471-2458-2-21.txt
-rwxr-xr-x  1 parthpaliwal  staff  29507 Feb  7 12:02 ./technical/biomed/1472-6793-3-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  20388 Feb  7 12:02 ./technical/biomed/1472-6963-3-13.txt
-rwxr-xr-x  1 parthpaliwal  staff  30676 Feb  7 12:02 ./technical/biomed/1471-2164-3-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  75711 Feb  7 12:02 ./technical/biomed/1471-2202-3-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  23490 Feb  7 12:02 ./technical/biomed/1471-2210-2-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  19877 Feb  7 12:02 ./technical/biomed/1471-2199-3-10.txt
-rwxr-xr-x  1 parthpaliwal  staff  15134 Feb  7 12:02 ./technical/biomed/1471-2350-2-12.txt
-rwxr-xr-x  1 parthpaliwal  staff  26118 Feb  7 12:02 ./technical/biomed/1471-2350-3-9.txt
-rwxr-xr-x  1 parthpaliwal  staff  43338 Feb  7 12:02 ./technical/biomed/1475-9268-1-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  36028 Feb  7 12:02 ./technical/biomed/gb-2001-2-2-research0004.txt
-rwxr-xr-x  1 parthpaliwal  staff  17840 Feb  7 12:02 ./technical/biomed/cc2160.txt
-rwxr-xr-x  1 parthpaliwal  staff  34558 Feb  7 12:02 ./technical/biomed/1472-6750-3-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  47766 Feb  7 12:02 ./technical/biomed/1471-2202-3-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  32319 Feb  7 12:02 ./technical/biomed/1471-2164-4-13.txt
-rwxr-xr-x  1 parthpaliwal  staff  54849 Feb  7 12:02 ./technical/biomed/1471-2091-3-14.txt
-rwxr-xr-x  1 parthpaliwal  staff  35587 Feb  7 12:02 ./technical/biomed/1471-5945-2-13.txt
-rwxr-xr-x  1 parthpaliwal  staff  29324 Feb  7 12:02 ./technical/biomed/1471-2164-3-32.txt
-rwxr-xr-x  1 parthpaliwal  staff  21046 Feb  7 12:02 ./technical/biomed/1471-2164-3-26.txt
-rwxr-xr-x  1 parthpaliwal  staff  30852 Feb  7 12:02 ./technical/biomed/1471-2288-2-11.txt
-rwxr-xr-x  1 parthpaliwal  staff  37694 Feb  7 12:02 ./technical/biomed/1471-2180-3-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  31799 Feb  7 12:02 ./technical/biomed/1472-6750-1-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  51187 Feb  7 12:02 ./technical/biomed/gb-2003-4-6-r39.txt
-rwxr-xr-x  1 parthpaliwal  staff  36580 Feb  7 12:02 ./technical/biomed/1471-2458-2-25.txt
-rwxr-xr-x  1 parthpaliwal  staff  51112 Feb  7 12:02 ./technical/biomed/gb-2003-4-3-r20.txt
-rwxr-xr-x  1 parthpaliwal  staff  35998 Feb  7 12:02 ./technical/biomed/gb-2003-4-9-r57.txt
-rwxr-xr-x  1 parthpaliwal  staff  34129 Feb  7 12:02 ./technical/biomed/1471-2121-3-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  20230 Feb  7 12:02 ./technical/biomed/1471-2407-2-23.txt
-rwxr-xr-x  1 parthpaliwal  staff  33821 Feb  7 12:02 ./technical/biomed/1471-2105-4-28.txt
-rwxr-xr-x  1 parthpaliwal  staff  42551 Feb  7 12:02 ./technical/biomed/1472-6947-2-7.txt
-rwxr-xr-x  1 parthpaliwal  staff  32848 Feb  7 12:02 ./technical/biomed/gb-2002-3-5-research0021.txt
-rwxr-xr-x  1 parthpaliwal  staff  27321 Feb  7 12:02 ./technical/biomed/ar407.txt
-rwxr-xr-x  1 parthpaliwal  staff  29608 Feb  7 12:02 ./technical/biomed/1471-2199-3-7.txt
-rwxr-xr-x  1 parthpaliwal  staff  35654 Feb  7 12:02 ./technical/biomed/1475-2867-3-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  21404 Feb  7 12:02 ./technical/biomed/1475-925X-2-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  23790 Feb  7 12:02 ./technical/biomed/1475-2867-3-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  34563 Feb  7 12:02 ./technical/biomed/1471-2105-3-34.txt
-rwxr-xr-x  1 parthpaliwal  staff  39368 Feb  7 12:02 ./technical/biomed/gb-2002-3-5-research0020.txt
-rwxr-xr-x  1 parthpaliwal  staff  22429 Feb  7 12:02 ./technical/biomed/1471-2407-2-22.txt
-rwxr-xr-x  1 parthpaliwal  staff  32852 Feb  7 12:02 ./technical/biomed/1471-2121-2-15.txt
-rwxr-xr-x  1 parthpaliwal  staff  14560 Feb  7 12:02 ./technical/biomed/1471-2148-2-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  19035 Feb  7 12:02 ./technical/biomed/cc1044.txt
-rwxr-xr-x  1 parthpaliwal  staff  28719 Feb  7 12:02 ./technical/biomed/1471-2091-4-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  25922 Feb  7 12:02 ./technical/biomed/1471-2288-1-9.txt
-rwxr-xr-x  1 parthpaliwal  staff  32562 Feb  7 12:02 ./technical/biomed/rr37.txt
-rwxr-xr-x  1 parthpaliwal  staff  60518 Feb  7 12:02 ./technical/biomed/gb-2001-3-1-research0001.txt
-rwxr-xr-x  1 parthpaliwal  staff  26929 Feb  7 12:02 ./technical/biomed/1472-6963-3-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  19565 Feb  7 12:02 ./technical/biomed/1471-2172-2-9.txt
-rwxr-xr-x  1 parthpaliwal  staff  16116 Feb  7 12:02 ./technical/biomed/1471-2458-2-18.txt
-rwxr-xr-x  1 parthpaliwal  staff  43688 Feb  7 12:02 ./technical/biomed/1471-2180-3-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  42772 Feb  7 12:02 ./technical/biomed/1471-2288-2-10.txt
-rwxr-xr-x  1 parthpaliwal  staff  45524 Feb  7 12:02 ./technical/biomed/1471-2164-3-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  20943 Feb  7 12:02 ./technical/biomed/1472-6793-3-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  22757 Feb  7 12:02 ./technical/biomed/gb-2002-3-12-research0075.txt
-rwxr-xr-x  1 parthpaliwal  staff  24329 Feb  7 12:02 ./technical/biomed/1471-2164-3-27.txt
-rwxr-xr-x  1 parthpaliwal  staff  32602 Feb  7 12:02 ./technical/biomed/1471-2164-3-33.txt
-rwxr-xr-x  1 parthpaliwal  staff  34209 Feb  7 12:02 ./technical/biomed/1471-2091-3-15.txt
-rwxr-xr-x  1 parthpaliwal  staff  32489 Feb  7 12:02 ./technical/biomed/1471-2202-3-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  47947 Feb  7 12:02 ./technical/biomed/1472-6750-2-14.txt
-rwxr-xr-x  1 parthpaliwal  staff  38765 Feb  7 12:02 ./technical/biomed/1471-2180-1-7.txt
-rwxr-xr-x  1 parthpaliwal  staff  16242 Feb  7 12:02 ./technical/biomed/cc1497.txt
-rwxr-xr-x  1 parthpaliwal  staff  22233 Feb  7 12:02 ./technical/biomed/1471-2334-2-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  22226 Feb  7 12:02 ./technical/biomed/1471-2199-3-17.txt
-rwxr-xr-x  1 parthpaliwal  staff  23338 Feb  7 12:02 ./technical/biomed/1471-2350-2-11.txt
-rwxr-xr-x  1 parthpaliwal  staff  27097 Feb  7 12:02 ./technical/biomed/1471-2334-2-7.txt
-rwxr-xr-x  1 parthpaliwal  staff  16376 Feb  7 12:02 ./technical/biomed/cc1495.txt
-rwxr-xr-x  1 parthpaliwal  staff  20942 Feb  7 12:02 ./technical/biomed/1475-9268-1-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  48259 Feb  7 12:02 ./technical/biomed/1477-7827-1-46.txt
-rwxr-xr-x  1 parthpaliwal  staff  29469 Feb  7 12:02 ./technical/biomed/1471-2091-3-17.txt
-rwxr-xr-x  1 parthpaliwal  staff  25350 Feb  7 12:02 ./technical/biomed/ar799.txt
-rwxr-xr-x  1 parthpaliwal  staff  33671 Feb  7 12:02 ./technical/biomed/1471-2164-3-19.txt
-rwxr-xr-x  1 parthpaliwal  staff  51726 Feb  7 12:02 ./technical/biomed/gb-2002-3-12-research0088.txt
-rwxr-xr-x  1 parthpaliwal  staff  40400 Feb  7 12:02 ./technical/biomed/1471-2164-3-31.txt
-rwxr-xr-x  1 parthpaliwal  staff  41682 Feb  7 12:02 ./technical/biomed/gb-2002-3-12-research0077.txt
-rwxr-xr-x  1 parthpaliwal  staff  41716 Feb  7 12:02 ./technical/biomed/1472-6963-3-14.txt
-rwxr-xr-x  1 parthpaliwal  staff  33494 Feb  7 12:02 ./technical/biomed/1475-2875-1-14.txt
-rwxr-xr-x  1 parthpaliwal  staff  21289 Feb  7 12:02 ./technical/biomed/1471-2164-3-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  20637 Feb  7 12:02 ./technical/biomed/gb-2003-4-8-r51.txt
-rwxr-xr-x  1 parthpaliwal  staff  29607 Feb  7 12:02 ./technical/biomed/1475-2875-2-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  21711 Feb  7 12:02 ./technical/biomed/1472-6963-1-11.txt
-rwxr-xr-x  1 parthpaliwal  staff  28204 Feb  7 12:02 ./technical/biomed/ar612.txt
-rwxr-xr-x  1 parthpaliwal  staff  28870 Feb  7 12:02 ./technical/biomed/1472-6793-2-19.txt
-rwxr-xr-x  1 parthpaliwal  staff  17629 Feb  7 12:02 ./technical/biomed/1471-230X-1-8.txt
-rwxr-xr-x  1 parthpaliwal  staff  19427 Feb  7 12:02 ./technical/biomed/1471-2148-2-7.txt
-rwxr-xr-x  1 parthpaliwal  staff  38544 Feb  7 12:02 ./technical/biomed/gb-2002-3-5-research0022.txt
-rwxr-xr-x  1 parthpaliwal  staff  46390 Feb  7 12:02 ./technical/biomed/1471-2288-3-9.txt
-rwxr-xr-x  1 parthpaliwal  staff  29117 Feb  7 12:02 ./technical/biomed/1471-2105-3-22.txt
-rwxr-xr-x  1 parthpaliwal  staff  33905 Feb  7 12:02 ./technical/biomed/1472-6947-2-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  23358 Feb  7 12:02 ./technical/biomed/bcr317.txt
-rwxr-xr-x  1 parthpaliwal  staff  17695 Feb  7 12:02 ./technical/biomed/1475-925X-2-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  30804 Feb  7 12:02 ./technical/biomed/bcr303.txt
-rwxr-xr-x  1 parthpaliwal  staff  30792 Feb  7 12:02 ./technical/biomed/1471-2105-3-23.txt
-rwxr-xr-x  1 parthpaliwal  staff  23191 Feb  7 12:02 ./technical/biomed/1471-2288-3-8.txt
-rwxr-xr-x  1 parthpaliwal  staff  22904 Feb  7 12:02 ./technical/biomed/bcr458.txt
-rwxr-xr-x  1 parthpaliwal  staff  29508 Feb  7 12:02 ./technical/biomed/1471-2105-3-37.txt
-rwxr-xr-x  1 parthpaliwal  staff  19700 Feb  7 12:02 ./technical/biomed/gb-2002-3-5-research0023.txt
-rwxr-xr-x  1 parthpaliwal  staff  45713 Feb  7 12:02 ./technical/biomed/1472-6793-2-18.txt
-rwxr-xr-x  1 parthpaliwal  staff  27688 Feb  7 12:02 ./technical/biomed/1471-2156-2-17.txt
-rwxr-xr-x  1 parthpaliwal  staff  21464 Feb  7 12:02 ./technical/biomed/1471-2369-4-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  25253 Feb  7 12:02 ./technical/biomed/ar149.txt
-rwxr-xr-x  1 parthpaliwal  staff  26711 Feb  7 12:02 ./technical/biomed/gb-2002-3-6-research0029.txt
-rwxr-xr-x  1 parthpaliwal  staff  29793 Feb  7 12:02 ./technical/biomed/1471-2121-1-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  34076 Feb  7 12:02 ./technical/biomed/1471-2180-1-34.txt
-rwxr-xr-x  1 parthpaliwal  staff  29369 Feb  7 12:02 ./technical/biomed/gb-2003-4-8-r50.txt
-rwxr-xr-x  1 parthpaliwal  staff  40413 Feb  7 12:02 ./technical/biomed/1471-2164-3-7.txt
-rwxr-xr-x  1 parthpaliwal  staff  18364 Feb  7 12:02 ./technical/biomed/1471-2164-3-30.txt
-rwxr-xr-x  1 parthpaliwal  staff  41831 Feb  7 12:02 ./technical/biomed/1471-2202-2-20.txt
-rwxr-xr-x  1 parthpaliwal  staff  35306 Feb  7 12:02 ./technical/biomed/1471-2164-3-24.txt
-rwxr-xr-x  1 parthpaliwal  staff  28821 Feb  7 12:02 ./technical/biomed/1471-2202-3-7.txt
-rwxr-xr-x  1 parthpaliwal  staff  35953 Feb  7 12:02 ./technical/biomed/1471-2091-3-16.txt
-rwxr-xr-x  1 parthpaliwal  staff  47848 Feb  7 12:02 ./technical/biomed/1471-2164-3-18.txt
-rwxr-xr-x  1 parthpaliwal  staff  36952 Feb  7 12:02 ./technical/biomed/1472-6750-3-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  32160 Feb  7 12:02 ./technical/biomed/1472-6793-1-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  33504 Feb  7 12:02 ./technical/biomed/1471-2334-2-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  46555 Feb  7 12:02 ./technical/biomed/1471-213X-1-15.txt
-rwxr-xr-x  1 parthpaliwal  staff  16150 Feb  7 12:02 ./technical/biomed/cc350.txt
-rwxr-xr-x  1 parthpaliwal  staff  19888 Feb  7 12:02 ./technical/biomed/1471-2148-3-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  22429 Feb  7 12:02 ./technical/biomed/bcr588.txt
-rwxr-xr-x  1 parthpaliwal  staff  23248 Feb  7 12:02 ./technical/biomed/1471-2199-2-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  21894 Feb  7 12:02 ./technical/biomed/1475-2867-2-7.txt
-rwxr-xr-x  1 parthpaliwal  staff  31378 Feb  7 12:02 ./technical/biomed/1468-6708-3-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  51597 Feb  7 12:02 ./technical/biomed/1471-2121-3-25.txt
-rwxr-xr-x  1 parthpaliwal  staff  17234 Feb  7 12:02 ./technical/biomed/1471-2334-3-12.txt
-rwxr-xr-x  1 parthpaliwal  staff  27415 Feb  7 12:02 ./technical/biomed/1471-2202-4-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  78507 Feb  7 12:02 ./technical/biomed/1472-6882-1-10.txt
-rwxr-xr-x  1 parthpaliwal  staff  46803 Feb  7 12:02 ./technical/biomed/1471-2121-3-19.txt
-rwxr-xr-x  1 parthpaliwal  staff  32085 Feb  7 12:02 ./technical/biomed/1471-2164-4-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  34915 Feb  7 12:02 ./technical/biomed/1471-2229-2-9.txt
-rwxr-xr-x  1 parthpaliwal  staff  29598 Feb  7 12:02 ./technical/biomed/gb-2002-3-9-research0049.txt
-rwxr-xr-x  1 parthpaliwal  staff  24239 Feb  7 12:02 ./technical/biomed/1471-2334-1-17.txt
-rwxr-xr-x  1 parthpaliwal  staff  32867 Feb  7 12:02 ./technical/biomed/1471-2180-2-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  11287 Feb  7 12:02 ./technical/biomed/cc973.txt
-rwxr-xr-x  1 parthpaliwal  staff  53072 Feb  7 12:02 ./technical/biomed/1471-2210-1-7.txt
-rwxr-xr-x  1 parthpaliwal  staff  24415 Feb  7 12:02 ./technical/biomed/1471-2326-2-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  35235 Feb  7 12:02 ./technical/biomed/1471-2180-2-16.txt
-rwxr-xr-x  1 parthpaliwal  staff  17621 Feb  7 12:02 ./technical/biomed/1471-2121-4-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  13689 Feb  7 12:02 ./technical/biomed/1471-213X-2-8.txt
-rwxr-xr-x  1 parthpaliwal  staff  25055 Feb  7 12:02 ./technical/biomed/1472-6793-1-12.txt
-rwxr-xr-x  1 parthpaliwal  staff  30658 Feb  7 12:02 ./technical/biomed/1471-2199-4-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  25184 Feb  7 12:02 ./technical/biomed/1471-2199-4-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  25926 Feb  7 12:02 ./technical/biomed/1471-2369-3-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  39804 Feb  7 12:02 ./technical/biomed/1471-2164-2-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  38924 Feb  7 12:02 ./technical/biomed/1471-2202-2-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  45928 Feb  7 12:02 ./technical/biomed/gb-2002-3-9-research0048.txt
-rwxr-xr-x  1 parthpaliwal  staff  23226 Feb  7 12:02 ./technical/biomed/1471-2229-2-8.txt
-rwxr-xr-x  1 parthpaliwal  staff  25832 Feb  7 12:02 ./technical/biomed/1471-2474-4-8.txt
-rwxr-xr-x  1 parthpaliwal  staff  35704 Feb  7 12:02 ./technical/biomed/1471-2121-3-18.txt
-rwxr-xr-x  1 parthpaliwal  staff  31620 Feb  7 12:02 ./technical/biomed/1472-6882-1-11.txt
-rwxr-xr-x  1 parthpaliwal  staff  6297 Feb  7 12:02 ./technical/biomed/1471-2334-3-13.txt
-rwxr-xr-x  1 parthpaliwal  staff  21676 Feb  7 12:02 ./technical/biomed/cvm-2-1-038.txt
-rwxr-xr-x  1 parthpaliwal  staff  56063 Feb  7 12:02 ./technical/biomed/1471-2121-3-30.txt
-rwxr-xr-x  1 parthpaliwal  staff  33991 Feb  7 12:02 ./technical/biomed/1471-2156-4-10.txt
-rwxr-xr-x  1 parthpaliwal  staff  20447 Feb  7 12:02 ./technical/biomed/1471-2199-2-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  21898 Feb  7 12:02 ./technical/biomed/1476-4598-1-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  38772 Feb  7 12:02 ./technical/biomed/1471-2172-2-10.txt
-rwxr-xr-x  1 parthpaliwal  staff  31043 Feb  7 12:02 ./technical/biomed/1471-2121-2-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  23010 Feb  7 12:02 ./technical/biomed/1477-7827-1-21.txt
-rwxr-xr-x  1 parthpaliwal  staff  35797 Feb  7 12:02 ./technical/biomed/1477-7827-1-23.txt
-rwxr-xr-x  1 parthpaliwal  staff  25430 Feb  7 12:02 ./technical/biomed/1475-2891-1-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  18114 Feb  7 12:02 ./technical/biomed/1468-6708-3-7.txt
-rwxr-xr-x  1 parthpaliwal  staff  32069 Feb  7 12:02 ./technical/biomed/1471-2199-2-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  36588 Feb  7 12:02 ./technical/biomed/1471-2105-1-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  55347 Feb  7 12:02 ./technical/biomed/gb-2002-3-10-research0052.txt
-rwxr-xr-x  1 parthpaliwal  staff  26021 Feb  7 12:02 ./technical/biomed/1471-2202-4-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  24252 Feb  7 12:02 ./technical/biomed/1471-2334-3-11.txt
-rwxr-xr-x  1 parthpaliwal  staff  24850 Feb  7 12:02 ./technical/biomed/1471-2164-4-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  25831 Feb  7 12:02 ./technical/biomed/cvm-2-6-278.txt
-rwxr-xr-x  1 parthpaliwal  staff  19679 Feb  7 12:02 ./technical/biomed/cvm-2-4-180.txt
-rwxr-xr-x  1 parthpaliwal  staff  47668 Feb  7 12:02 ./technical/biomed/1471-2105-3-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  55181 Feb  7 12:02 ./technical/biomed/gb-2003-4-2-r9.txt
-rwxr-xr-x  1 parthpaliwal  staff  24661 Feb  7 12:02 ./technical/biomed/1475-2883-2-11.txt
-rwxr-xr-x  1 parthpaliwal  staff  22387 Feb  7 12:02 ./technical/biomed/1475-2867-2-10.txt
-rwxr-xr-x  1 parthpaliwal  staff  30961 Feb  7 12:02 ./technical/biomed/1471-2202-2-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  19094 Feb  7 12:02 ./technical/biomed/bcr602.txt
-rwxr-xr-x  1 parthpaliwal  staff  20538 Feb  7 12:02 ./technical/biomed/1471-2180-2-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  48870 Feb  7 12:02 ./technical/biomed/gb-2001-2-12-research0055.txt
-rwxr-xr-x  1 parthpaliwal  staff  35659 Feb  7 12:02 ./technical/biomed/1478-1336-1-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  31160 Feb  7 12:02 ./technical/biomed/1472-6793-2-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  33669 Feb  7 12:02 ./technical/biomed/1471-2210-1-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  52697 Feb  7 12:02 ./technical/biomed/1471-2091-3-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  34571 Feb  7 12:02 ./technical/biomed/1471-2121-4-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  34914 Feb  7 12:02 ./technical/biomed/gb-2002-3-4-research0019.txt
-rwxr-xr-x  1 parthpaliwal  staff  23827 Feb  7 12:02 ./technical/biomed/1471-2202-3-10.txt
-rwxr-xr-x  1 parthpaliwal  staff  13909 Feb  7 12:02 ./technical/biomed/1471-2180-2-29.txt
-rwxr-xr-x  1 parthpaliwal  staff  22140 Feb  7 12:02 ./technical/biomed/1472-6750-2-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  23183 Feb  7 12:02 ./technical/biomed/1476-511X-2-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  15211 Feb  7 12:02 ./technical/biomed/cc1547.txt
-rwxr-xr-x  1 parthpaliwal  staff  28809 Feb  7 12:02 ./technical/biomed/1472-6793-1-11.txt
-rwxr-xr-x  1 parthpaliwal  staff  14795 Feb  7 12:02 ./technical/biomed/1471-2407-2-9.txt
-rwxr-xr-x  1 parthpaliwal  staff  18174 Feb  7 12:02 ./technical/biomed/1471-2407-2-8.txt
-rwxr-xr-x  1 parthpaliwal  staff  35675 Feb  7 12:02 ./technical/biomed/1476-4598-2-28.txt
-rwxr-xr-x  1 parthpaliwal  staff  28467 Feb  7 12:02 ./technical/biomed/1476-511X-2-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  31287 Feb  7 12:02 ./technical/biomed/1471-2202-3-11.txt
-rwxr-xr-x  1 parthpaliwal  staff  37156 Feb  7 12:02 ./technical/biomed/1471-2121-4-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  29148 Feb  7 12:02 ./technical/biomed/gb-2002-3-4-research0018.txt
-rwxr-xr-x  1 parthpaliwal  staff  25902 Feb  7 12:02 ./technical/biomed/1471-2261-2-11.txt
-rwxr-xr-x  1 parthpaliwal  staff  33228 Feb  7 12:02 ./technical/biomed/1472-6793-2-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  37800 Feb  7 12:02 ./technical/biomed/1471-2164-2-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  40003 Feb  7 12:02 ./technical/biomed/gb-2001-2-12-research0054.txt
-rwxr-xr-x  1 parthpaliwal  staff  37212 Feb  7 12:02 ./technical/biomed/ar104.txt
-rwxr-xr-x  1 parthpaliwal  staff  37667 Feb  7 12:02 ./technical/biomed/1471-2407-1-15.txt
-rwxr-xr-x  1 parthpaliwal  staff  18827 Feb  7 12:02 ./technical/biomed/1471-2202-2-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  43710 Feb  7 12:02 ./technical/biomed/gb-2003-4-2-r8.txt
-rwxr-xr-x  1 parthpaliwal  staff  16536 Feb  7 12:02 ./technical/biomed/1472-6947-1-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  136424 Feb  7 12:02 ./technical/biomed/1471-2105-3-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  37128 Feb  7 12:02 ./technical/biomed/1471-2229-2-11.txt
-rwxr-xr-x  1 parthpaliwal  staff  54077 Feb  7 12:02 ./technical/biomed/1471-2164-4-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  19340 Feb  7 12:02 ./technical/biomed/cvm-2-6-286.txt
-rwxr-xr-x  1 parthpaliwal  staff  23842 Feb  7 12:02 ./technical/biomed/1471-2148-1-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  30506 Feb  7 12:02 ./technical/biomed/1471-2334-3-10.txt
-rwxr-xr-x  1 parthpaliwal  staff  31937 Feb  7 12:02 ./technical/biomed/1472-6882-1-12.txt
-rwxr-xr-x  1 parthpaliwal  staff  31808 Feb  7 12:02 ./technical/biomed/gb-2002-3-10-research0053.txt
-rwxr-xr-x  1 parthpaliwal  staff  10530 Feb  7 12:02 ./technical/biomed/1471-2156-2-8.txt
-rwxr-xr-x  1 parthpaliwal  staff  37082 Feb  7 12:02 ./technical/biomed/rr196.txt
-rwxr-xr-x  1 parthpaliwal  staff  45044 Feb  7 12:02 ./technical/biomed/1471-2148-3-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  19498 Feb  7 12:02 ./technical/biomed/1472-6807-2-9.txt
-rwxr-xr-x  1 parthpaliwal  staff  53800 Feb  7 12:02 ./technical/biomed/1477-7827-1-36.txt
-rwxr-xr-x  1 parthpaliwal  staff  40153 Feb  7 12:02 ./technical/biomed/1471-2148-3-7.txt
-rwxr-xr-x  1 parthpaliwal  staff  36535 Feb  7 12:02 ./technical/biomed/1471-213X-1-13.txt
-rwxr-xr-x  1 parthpaliwal  staff  26820 Feb  7 12:02 ./technical/biomed/1471-2121-2-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  31929 Feb  7 12:02 ./technical/biomed/gb-2002-3-3-research0012.txt
-rwxr-xr-x  1 parthpaliwal  staff  13363 Feb  7 12:02 ./technical/biomed/1471-2156-3-22.txt
-rwxr-xr-x  1 parthpaliwal  staff  21426 Feb  7 12:02 ./technical/biomed/bcr571.txt
-rwxr-xr-x  1 parthpaliwal  staff  54313 Feb  7 12:02 ./technical/biomed/1471-2199-2-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  28019 Feb  7 12:02 ./technical/biomed/gb-2000-1-2-research0003.txt
-rwxr-xr-x  1 parthpaliwal  staff  22981 Feb  7 12:02 ./technical/biomed/1472-6955-2-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  34496 Feb  7 12:02 ./technical/biomed/1471-2105-3-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  24615 Feb  7 12:02 ./technical/biomed/1471-2474-3-23.txt
-rwxr-xr-x  1 parthpaliwal  staff  33487 Feb  7 12:02 ./technical/biomed/1472-6947-1-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  26367 Feb  7 12:02 ./technical/biomed/1471-2407-3-14.txt
-rwxr-xr-x  1 parthpaliwal  staff  23922 Feb  7 12:02 ./technical/biomed/1471-2202-2-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  25953 Feb  7 12:02 ./technical/biomed/1475-2867-2-15.txt
-rwxr-xr-x  1 parthpaliwal  staff  30811 Feb  7 12:02 ./technical/biomed/1472-6793-2-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  20507 Feb  7 12:02 ./technical/biomed/gb-2002-3-8-research0039.txt
-rwxr-xr-x  1 parthpaliwal  staff  18646 Feb  7 12:02 ./technical/biomed/1471-2369-3-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  20662 Feb  7 12:02 ./technical/biomed/bcr607.txt
-rwxr-xr-x  1 parthpaliwal  staff  18987 Feb  7 12:02 ./technical/biomed/1472-6874-2-8.txt
-rwxr-xr-x  1 parthpaliwal  staff  24381 Feb  7 12:02 ./technical/biomed/1471-2180-2-7.txt
-rwxr-xr-x  1 parthpaliwal  staff  20730 Feb  7 12:02 ./technical/biomed/1471-2164-2-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  21154 Feb  7 12:02 ./technical/biomed/1471-2180-2-38.txt
-rwxr-xr-x  1 parthpaliwal  staff  16141 Feb  7 12:02 ./technical/biomed/1471-2210-3-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  21527 Feb  7 12:02 ./technical/biomed/1471-2431-2-11.txt
-rwxr-xr-x  1 parthpaliwal  staff  33137 Feb  7 12:02 ./technical/biomed/1472-6793-1-15.txt
-rwxr-xr-x  1 parthpaliwal  staff  22386 Feb  7 12:02 ./technical/biomed/1471-2458-3-9.txt
-rwxr-xr-x  1 parthpaliwal  staff  26467 Feb  7 12:02 ./technical/biomed/1471-2121-4-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  33896 Feb  7 12:02 ./technical/biomed/1471-2202-3-14.txt
-rwxr-xr-x  1 parthpaliwal  staff  32543 Feb  7 12:02 ./technical/biomed/1471-2164-2-7.txt
-rwxr-xr-x  1 parthpaliwal  staff  37186 Feb  7 12:02 ./technical/biomed/gb-2001-2-12-research0051.txt
-rwxr-xr-x  1 parthpaliwal  staff  45876 Feb  7 12:02 ./technical/biomed/gb-2002-3-8-research0038.txt
-rwxr-xr-x  1 parthpaliwal  staff  20900 Feb  7 12:02 ./technical/biomed/1471-244X-3-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  27117 Feb  7 12:02 ./technical/biomed/1471-2202-2-7.txt
-rwxr-xr-x  1 parthpaliwal  staff  16775 Feb  7 12:02 ./technical/biomed/1471-2334-1-10.txt
-rwxr-xr-x  1 parthpaliwal  staff  25312 Feb  7 12:02 ./technical/biomed/1471-2407-3-15.txt
-rwxr-xr-x  1 parthpaliwal  staff  33441 Feb  7 12:02 ./technical/biomed/1471-2121-3-22.txt
-rwxr-xr-x  1 parthpaliwal  staff  35377 Feb  7 12:02 ./technical/biomed/1471-2334-3-15.txt
-rwxr-xr-x  1 parthpaliwal  staff  29837 Feb  7 12:02 ./technical/biomed/1471-2148-1-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  34740 Feb  7 12:02 ./technical/biomed/1471-2199-2-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  16882 Feb  7 12:02 ./technical/biomed/1468-6708-3-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  20468 Feb  7 12:02 ./technical/biomed/bcr570.txt
-rwxr-xr-x  1 parthpaliwal  staff  45288 Feb  7 12:02 ./technical/biomed/gb-2002-3-10-research0056.txt
-rwxr-xr-x  1 parthpaliwal  staff  30395 Feb  7 12:02 ./technical/biomed/1472-6947-3-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  23825 Feb  7 12:02 ./technical/biomed/cc343.txt
-rwxr-xr-x  1 parthpaliwal  staff  29734 Feb  7 12:02 ./technical/biomed/1471-213X-1-12.txt
-rwxr-xr-x  1 parthpaliwal  staff  28483 Feb  7 12:02 ./technical/biomed/1471-2296-3-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  25530 Feb  7 12:02 ./technical/biomed/1477-7827-1-27.txt
-rwxr-xr-x  1 parthpaliwal  staff  15245 Feb  7 12:02 ./technical/biomed/1476-4598-1-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  30791 Feb  7 12:02 ./technical/biomed/rr191.txt
-rwxr-xr-x  1 parthpaliwal  staff  33162 Feb  7 12:02 ./technical/biomed/1471-2148-3-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  35574 Feb  7 12:02 ./technical/biomed/1471-2458-3-11.txt
-rwxr-xr-x  1 parthpaliwal  staff  31562 Feb  7 12:02 ./technical/biomed/1475-2875-1-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  41600 Feb  7 12:02 ./technical/biomed/1477-7827-1-31.txt
-rwxr-xr-x  1 parthpaliwal  staff  26832 Feb  7 12:02 ./technical/biomed/1471-213X-1-10.txt
-rwxr-xr-x  1 parthpaliwal  staff  46710 Feb  7 12:02 ./technical/biomed/gb-2002-3-3-research0011.txt
-rwxr-xr-x  1 parthpaliwal  staff  32878 Feb  7 12:02 ./technical/biomed/gb-2002-3-10-research0054.txt
-rwxr-xr-x  1 parthpaliwal  staff  24112 Feb  7 12:02 ./technical/biomed/1468-6708-3-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  12833 Feb  7 12:02 ./technical/biomed/1471-2148-1-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  32938 Feb  7 12:02 ./technical/biomed/1471-2202-4-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  18158 Feb  7 12:02 ./technical/biomed/1472-6947-1-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  32780 Feb  7 12:02 ./technical/biomed/1471-2202-2-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  37006 Feb  7 12:02 ./technical/biomed/1476-9433-1-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  14603 Feb  7 12:02 ./technical/biomed/1471-2210-1-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  32387 Feb  7 12:02 ./technical/biomed/1471-2458-1-9.txt
-rwxr-xr-x  1 parthpaliwal  staff  35125 Feb  7 12:02 ./technical/biomed/1472-6793-2-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  25094 Feb  7 12:02 ./technical/biomed/gb-2001-2-12-research0053.txt
-rwxr-xr-x  1 parthpaliwal  staff  22678 Feb  7 12:02 ./technical/biomed/1478-1336-1-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  42803 Feb  7 12:02 ./technical/biomed/1471-2202-3-16.txt
-rwxr-xr-x  1 parthpaliwal  staff  28049 Feb  7 12:02 ./technical/biomed/1471-2180-2-13.txt
-rwxr-xr-x  1 parthpaliwal  staff  25444 Feb  7 12:02 ./technical/biomed/1471-2121-4-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  28895 Feb  7 12:02 ./technical/biomed/gb-2003-4-4-r28.txt
-rwxr-xr-x  1 parthpaliwal  staff  11200 Feb  7 12:02 ./technical/biomed/1471-230X-2-17.txt
-rwxr-xr-x  1 parthpaliwal  staff  21459 Feb  7 12:02 ./technical/biomed/1477-5956-1-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  43248 Feb  7 12:02 ./technical/biomed/1471-2156-4-9.txt
-rwxr-xr-x  1 parthpaliwal  staff  26239 Feb  7 12:02 ./technical/biomed/1471-2431-2-12.txt
-rwxr-xr-x  1 parthpaliwal  staff  15903 Feb  7 12:02 ./technical/biomed/ar328.txt
-rwxr-xr-x  1 parthpaliwal  staff  28562 Feb  7 12:02 ./technical/biomed/1471-2210-3-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  27586 Feb  7 12:02 ./technical/biomed/1471-2121-4-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  11237 Feb  7 12:02 ./technical/biomed/1471-2350-2-8.txt
-rwxr-xr-x  1 parthpaliwal  staff  29638 Feb  7 12:02 ./technical/biomed/1471-2202-3-17.txt
-rwxr-xr-x  1 parthpaliwal  staff  23484 Feb  7 12:02 ./technical/biomed/1471-2407-1-13.txt
-rwxr-xr-x  1 parthpaliwal  staff  46272 Feb  7 12:02 ./technical/biomed/bcr605.txt
-rwxr-xr-x  1 parthpaliwal  staff  74965 Feb  7 12:02 ./technical/biomed/1476-069X-2-9.txt
-rwxr-xr-x  1 parthpaliwal  staff  23526 Feb  7 12:02 ./technical/biomed/1478-1336-1-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  27684 Feb  7 12:02 ./technical/biomed/1471-2164-2-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  28252 Feb  7 12:02 ./technical/biomed/1471-2210-1-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  21318 Feb  7 12:02 ./technical/biomed/1476-9433-1-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  21797 Feb  7 12:02 ./technical/biomed/1471-2334-1-13.txt
-rwxr-xr-x  1 parthpaliwal  staff  22447 Feb  7 12:02 ./technical/biomed/1471-2407-3-16.txt
-rwxr-xr-x  1 parthpaliwal  staff  28119 Feb  7 12:02 ./technical/biomed/1471-2164-4-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  25609 Feb  7 12:02 ./technical/biomed/cvm-2-4-187.txt
-rwxr-xr-x  1 parthpaliwal  staff  34817 Feb  7 12:02 ./technical/biomed/1471-2105-3-4.txt
-rwxr-xr-x  1 parthpaliwal  staff  32262 Feb  7 12:02 ./technical/biomed/1471-2121-3-21.txt
-rwxr-xr-x  1 parthpaliwal  staff  33888 Feb  7 12:02 ./technical/biomed/1471-2202-4-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  21927 Feb  7 12:02 ./technical/biomed/1471-2172-3-9.txt
-rwxr-xr-x  1 parthpaliwal  staff  23524 Feb  7 12:02 ./technical/biomed/gb-2001-2-3-research0007.txt
-rwxr-xr-x  1 parthpaliwal  staff  26704 Feb  7 12:02 ./technical/biomed/1471-2199-2-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  16229 Feb  7 12:02 ./technical/biomed/bcr567.txt
-rwxr-xr-x  1 parthpaliwal  staff  47650 Feb  7 12:02 ./technical/biomed/gb-2002-3-10-research0055.txt
-rwxr-xr-x  1 parthpaliwal  staff  14165 Feb  7 12:02 ./technical/biomed/1471-2121-2-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  29630 Feb  7 12:02 ./technical/biomed/1471-213X-1-11.txt
-rwxr-xr-x  1 parthpaliwal  staff  49884 Feb  7 12:02 ./technical/biomed/1472-684X-1-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  33139 Feb  7 12:02 ./technical/biomed/1476-4598-1-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  265912 Feb  7 12:02 ./technical/911report/chapter-13.4.txt
-rwxr-xr-x  1 parthpaliwal  staff  290993 Feb  7 12:02 ./technical/911report/chapter-13.5.txt
-rwxr-xr-x  1 parthpaliwal  staff  89854 Feb  7 12:02 ./technical/911report/chapter-13.1.txt
-rwxr-xr-x  1 parthpaliwal  staff  110568 Feb  7 12:02 ./technical/911report/chapter-13.2.txt
-rwxr-xr-x  1 parthpaliwal  staff  150467 Feb  7 12:02 ./technical/911report/chapter-13.3.txt
-rwxr-xr-x  1 parthpaliwal  staff  264360 Feb  7 12:02 ./technical/911report/chapter-3.txt
-rwxr-xr-x  1 parthpaliwal  staff  79803 Feb  7 12:02 ./technical/911report/chapter-2.txt
-rwxr-xr-x  1 parthpaliwal  staff  118656 Feb  7 12:02 ./technical/911report/chapter-1.txt
-rwxr-xr-x  1 parthpaliwal  staff  99008 Feb  7 12:02 ./technical/911report/chapter-5.txt
-rwxr-xr-x  1 parthpaliwal  staff  149063 Feb  7 12:02 ./technical/911report/chapter-6.txt
-rwxr-xr-x  1 parthpaliwal  staff  128370 Feb  7 12:02 ./technical/911report/chapter-7.txt
-rwxr-xr-x  1 parthpaliwal  staff  149644 Feb  7 12:02 ./technical/911report/chapter-9.txt
-rwxr-xr-x  1 parthpaliwal  staff  84835 Feb  7 12:02 ./technical/911report/chapter-8.txt
-rwxr-xr-x  1 parthpaliwal  staff  9332 Feb  7 12:02 ./technical/911report/preface.txt
-rwxr-xr-x  1 parthpaliwal  staff  127587 Feb  7 12:02 ./technical/911report/chapter-12.txt
-rwxr-xr-x  1 parthpaliwal  staff  47307 Feb  7 12:02 ./technical/911report/chapter-10.txt
-rwxr-xr-x  1 parthpaliwal  staff  71151 Feb  7 12:02 ./technical/911report/chapter-11.txt
```

### Example 8: ```find ./technical -type d -exec ls -ld {} \;```
executes the ls -ld command on each directory found within the ./technical directory and its subdirectories.

Output:
```
drwxrwxr-x  7 parthpaliwal  staff  224 Feb 13 17:47 ./technical
drwxrwxr-x  8 parthpaliwal  staff  256 Feb  7 12:02 ./technical/government
drwxrwxr-x  19 parthpaliwal  staff  608 Feb  7 12:02 ./technical/government/About_LSC
drwxrwxr-x  16 parthpaliwal  staff  512 Feb  7 12:02 ./technical/government/Env_Prot_Agen
drwxrwxr-x  6 parthpaliwal  staff  192 Feb  7 12:02 ./technical/government/Alcohol_Problems
drwxrwxr-x  93 parthpaliwal  staff  2976 Feb  7 12:02 ./technical/government/Gen_Account_Office
drwxrwxr-x  16 parthpaliwal  staff  512 Feb  7 12:02 ./technical/government/Post_Rate_Comm
drwxrwxr-x  147 parthpaliwal  staff  4704 Feb  7 12:02 ./technical/government/Media
drwxrwxr-x  254 parthpaliwal  staff  8128 Feb  7 12:02 ./technical/plos
drwxrwxr-x  839 parthpaliwal  staff  26848 Feb  7 12:02 ./technical/biomed
drwxrwxr-x  19 parthpaliwal  staff  608 Feb  7 12:02 ./technical/911report
```
