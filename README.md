# Sublime-Text-Setup

## 1. Install MinGW Compiler
MinGW is a native Windows port of the GNU Compiler Collection (GCC). Install the latest MinGW compiler, after downloading from here.
Your path should preferably be C:\MinGW. Finally, add the bin directory, C:\MinGW\bin to the System PATH.

## 2. Install Sublime Text
Sublime Text is one of the most popular editors for development in general. 
It’s smooth and fast compared to other editors (being written in C++ helps that speed). 
Sublime also has tons of plugins you can find through Package Control. Download and install Sublime Text 3 from here.
https://www.sublimetext.com/3

## 3. Create a build system
Sublime Text provides build systems to allow users to run external programs. Create a new build system for Sublime Text for setting up C++ compilation.
Go to Tools > Build System > New Build System. Paste the following code in the file and save it.
```
{
"cmd": ["g++.exe","-std=c++17", "${file}", "-o", "${file_base_name}.exe", "&&" , "${file_base_name}.exe<inputf.in>outputf.in"],
"shell":true,
"working_dir":"$file_path",
"selector":"source.cpp"
}
```
This can be used for piping input from the inputf.in file, and output to the outputf.in file. 
Note that this uses the -std=c++17 flag to enable the latest features of C++17. 
If you don't want this or want to use C++14, replace this with the -std=c++14 flag.

## 4. Setup window layout
Create three new files, file.cpp, inputf.in, and outputf.in. Select View > Layout > Columns : 3. 
This will create three columns in the workspace. Move the three files into the three columns. Select View > Groups > Max Columns : 2.


![alt text](https://github.com/Chet8n/Sublime-Text-Setup/blob/master/Screenshot%20(211).png)


The windows will look like above when you are done. Write a hello world program, and test its working. Use Ctrl+B to build and execute the file.

## 5. Precompile headers
Now we can speed up compilation time by precompiling all the header files as mentioned [here](https://codeforces.com/blog/entry/53909), i.e. 
by precompiling the bits/stdc++.h header file. This can speed up compilation time by up to a factor of 12.
For this, first, navigate to the stdc++.h file. This will be located at a directory similar 
to C:\MinGW\lib\gcc\mingw32\6.3.0\include\c++\mingw32\bits. 
Right click while pressing Shift to open a Powershell/cmd window there. Run the command g++ -std=c++17 stdc++.h, 
to compile the header. Take care to use the same flags you used in your build system. Check to make sure that the stdc++.h.gch file was created in the directory.

Finally, we can take advantage of the features of Sublime Text, namely snippets and completions.
