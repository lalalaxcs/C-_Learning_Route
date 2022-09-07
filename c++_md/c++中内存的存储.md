# c++中内存的存储

## 一.内存的结构

### 1.内存分为一下四个区域:

- 代码区
- 全局区
- 栈区
- 堆区

### 2.代码区

存放的是函数体的2进制代码，由操作系统进行管理

### 3.全局区

存放的是全局变量，静态变量，全局常量、字符串常量

### 4.栈区

存放函数的参数值，局部变量 有编译器自动分配释放

### 5.堆区

由程序员分配和释放 如果程序员不释放，程序结束后由操作系统回收

### 6、内存结构图

![asd](C:\Users\1\Desktop\md\c++\image\u=3611386421,1511314199&fm=253&fmt=auto&app=138&f=JPEG.webp)





## 二.变量的存储

### 1、变量的类型

- 全局变量 存放在全局区中
- 局部变量 存放在栈区中
- 静态变量 存放在全局区中

### 2、代码演示

```c++
#include <iosteam>
useing namespace std;
int num1 = 10;
int main(){
    int num2  = 10;
    static int num3 = 10;
    cout << "全局变量的地址是" << (int)&num1;
    cout << "局部变量的地址是" << (int)&num2;
    cout << "静态变量的地址是" << (int)&num3;
    system("pause");
    return 0;
}

```

<img src="C:\Users\1\Desktop\md\c++\image\QQ截图20220820123330.png" style="zoom:200%;" />

可以看到 全局变量和静态变量都在接近的位置 而局部变量离得较远

## 三.常量的存储

### 1.常量的类型

- 全局常量
- 局部变量
- 字符串常量

### 2.代码演示

```c++
#include <iosteam>
useing namespace std;
const int a= 10;
int num1 = 10;
int main(){
    const int b = 10;
    int num2  = 10;
    static int num3 = 10;
    cout << "全局变量的地址是" << (int)&num1 << endl;
    cout << "局部变量的地址是" << (int)&num2 << endl;
    cout << "静态变量的地址是" << (int)&num3 << endl;
    cout << "全局常量的地址是" << (int)&a << endl;
    cout << "局部常量的地址是" << (int)&b << endl;
    cout << "字符串常量的地址是" << (int)&"hello world" << endl;
    system("pause");
    return 0;
}
```

<img src="C:\Users\1\Desktop\md\c++\image\QQ截图20220821003831.png" style="zoom: 200%;" />

#### 3.结论

​	可以看到 全局变量、静态变量、字符串常量、全局常量存放的地址都非常接近，都存放在全局区

​	而局部变量和局部常量的地址比较接近，都存放在栈区

## 四、栈区的开辟和释放

### 1.概念

栈区是由编译器所管理的地区

### 2.注意事项

不要在返回局部变量的地址

```c++
int * fun1(){
    int a = 10;
    return &a;
}
int main(){
    int * p =fun1();
    cout <<"局部变量的地址是:"<<p<<endl;
    cout <<"局部变量的地址是:"<<p<<endl;
}
```



