# 多项式
## 多项式的表达和创建
在MATLAB中，多项式表示成向量的形式，它的系数是按降序排列的。只需要将按降幂次序的多项式的每个系数填入向量中，就可以在MATLAB中建立一个多项式。

1. 多项式相加，即`c(x)=a(x)+b(x)`
2. 多项式相减，即`C(x)=a(x)-b(x)`
3. 多项式相乘，即`C(X)=A(x)B(x)`
4. 多项式相除，即`C(x)=a(x)/b(x)`

多项式的加减在检测相同的情况下可以直接运算，  
若两个相加减的多项式阶次不同，则低阶多项式必须用零填补高阶项系数，  
使其与高阶多项式有相同的阶次。而且通常情况下，  
进行加减的两个多项式的阶次不会相同，这时可以自定义一个函数`polyadd`来完成两个多像是的相加。  
```
function [poly]=polyadd(poly1,poly2)
%polyadd(poly1,poly2) adds two polynominals possibly of uneven length
if length(poly1)<length(poly2)
      short=poly1;
      long=poly2;
else
      short=poly2;
      long=poly1;
end
mz=length(long)-length(short);
if mz>0
      poly=[zeros(1,mz),short]+long;
else
      poly=long+short;
end

```

这个函数生成polyadd.m文件，并将该文件保存在MATLAB搜索路径中的一个目录下，这样polyadd  
函数就可以和MATLAB工具箱中其他函数一样使用了。


多项式相乘是一个卷积的过程，当两个多项式相乘时，
可以通过计算两个多项式的系数的卷积来完成。MATLAB
中函数conv可完成此功能。函数conv的语法为c=conv(a,b),其中a,b代表两个多项式的系数向量，  函数conv也可以嵌套使用，如conv(conv(a,b),c).

多项式的除法是乘法的逆过程，利用函数deconv可以返回相除的余数和商多项式。函数deconv的语法为[q,r]=deconv(a,b),其中q,r分别代表整除多项式及余数多项式。  

## 多项式求值和求根运算

> 多项式求值

在MATLAB中,可以用函数polyval来进行多项式求值运算。函数polyval常用的一种语法格式  
```
y=polyval(p,x)

```
其中p代表多项式各阶系数向量，x为要求值得点。当x表示矩阵时，需要用y=polyvalm(p,x)
来计算相应的值。

> 多项式的构造

在MATLAB中可利用符号工具箱中的函数poly2sym来构造多项式，  
也可用函数poly来求根对应的多项式的各阶系数。  

### 所涉及到的多项式函数

|  |  |
| ------| :------: | 
| conv(a,b) | 乘法 |
| [q,r]=deconv(a,b) | 除法  |
| poly(R)| 用根构造多项式|
|polyadd(x,y)| 加法 |
|polyval(p,x)| 计算x点中多项式值|
|poly2sym(p)|将系数多项式变成符号多项式|
|roots(a)|求多项式的根|
