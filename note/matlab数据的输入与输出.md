# 数据的输入与输出

### 键盘输入语句
1. x=input('prompt');显示提示字符串'prompt'，要求用户键盘输入x的值。

2. x=input('prompt','s');显示提示字符串'prompt'，要求用户键盘输入字符型变量值,不  至于将输入的数字看成是数值型数据。

### 屏幕输出语句(disp)
屏幕输出直接写出欲输出的变量名称或数值名,后面不加分号。  
disp(x).


## M数据文件的存储/加载
1. save语句  

  * save: 将工作空间变量存储在名为MATLAB.mat文件中
  * save filename:将所用工作空间变量存储才名为filename的文件中
  * save filename X Y Z:将工作空间的指定变量X.Y.Z存储名为filename的文件中

2. load语句

  * load：如果 MATLAB.mat 文件存在，则加载 MATLAB.mat 文件中存储的所有变量
到工作空间；否则返回一错误信息。
  * load filename：如果 filename 文件存在，则加载 filename 文件中存储的所有变量到
工作空间；否则返回一错误信息。
  * load filename X Y Z：如果 filename 文件及存储的变量 X、Y、Z 存在，则加载 filename
文件中存储的变量 X、Y、Z 到工作空间；否则返回一错误信息

## fprint/fscanf
1. fprintf 语句  
其调用格式为 count = fprintf(fid,format,A,...) ，它将用 format 定义的格式化文本文件写
入以fopen打开的文件(打开文件标识符为文件句柄fid)，返回值count为写入文件的字节数。  
2. fscanf 语句
其调用格式有
  * A = fscanf(fid,format)：读取以 fid 指定的文件数据，并将它转换为 format 定义的格
式化文本，然后赋给变量 A。
  * [A,count] = fscanf(fid,format,size)：读取以 fid 指定的文件数据，读取的数据限定为
size 字节，并将它转换为 format 定义的格式化文本，然后赋给变量 A；同时返回有效读取
数据的字节数 count。

## fwrite/ fread
1. fwrite 语句
其调用格式为 count = fwrite(fid,A,precision)，它将用 precision 指定的精度，将数组 A
的元素写入以 fid 指定的文件，返回值 count 为成功写入文件的元素数。
2. fread 语句
其调用格式为[A,count] = fread(fid,size,precision)，读取以 fid 指定的文件中的数组元素，
并转换为 precision 指定的精度，赋给数组 A。返回值 count 为成功读取数组的元素数。

## fgetl / fgets
1. fgetl 语句
其调用格式为 tline = fgetl(fid)，读取以 fid 指定的文件中的下一行数据，不包括回车符。
2. fgets 语句
其调用格式有
  * tline = fgets(fid)：读取以 fid 指定的文件中的下一行数据，包括回车符。
  * tline = fgets(fid,nchar)：读取以 fid 指定的文件中的下一行数据，最多读取 nchar 个
字符，如果遇到回车符则不再读取数据。
