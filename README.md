# c-p78C-3-
C语言学习笔记p78C语言预处理（3）


C语言
C语言实现数据结构（简单数据结构）：顺序表、链表、栈、队列、二叉树及相关面试题
C++           Linux系统：网络+网络编程
高级数据结构    MySQL


#define后面不需要➕分号，有时可能会出错
#define定义宏
#define机制包括了一个规定，允许把参数替换(不是传参)到文本中，这种实现通常称为宏或定义宏
#define SQUARE(X) (X)*(X)//写宏不要吝啬括号
#include<stdio.h>
int main()
{
      int ret=SQUARE(5);//这里就会替换到括号后面的定义相当于5*5
      int ret=5*5;//25
      return 0;
}
写宏不要吝啬括号
#define DOUBLE(X) X+X
int main()
{
      int a=5;
      int ret=10*DOUBLE(a);//此时输出为55，输出不尽人意
      
      return 0;
}


#define 替换规则
1.在调用宏时，首先对参数进行检查，看看是否包含任何由#define定义的符号，如果是，他们首先被替换。
例：
    #define MAX 100
    #define DOUBLE(X) ((X)+(X))
    int main()
    {
          int a=5;
          int ret=10*DOUBLE(MAX)//这里MAX首先被替换
          return 0;
          
    }

2.替换文本随后被插入到程序中的原来文本的位置，对于定义宏，参数名被他们的值替换。
3.最后，再次对结果进行扫描，看看它是否包含任何由#define定义的符号，如果是，就重复上述处理过程。


注：#define定义的变量可以出现在其它#define定义的变量中，但宏不可以递归


如何把参数插入到字符串中？
使用#，把一个宏参数变成对应的字符串
#define PRINT(X) printf("the value of “#X” is%d",x)
int main()
{
      int a=10;
      int b=20;
      PRINT(a);
      //printf("the value of"a" is %d\n",a);
      PRINT(b);
      //printf("the value of"b" is %d\n",b);
      return 0;
}


##可以把位于它两边的符号合成一个符号，它允许宏定义从分离的文本片段创建标识符
#define CAT(X,Y) X##Y
int main()
{
      int class84=2019;
      //printf("%d\n",Class84);
      printf("%d\n",CAT(Class,84));
      //printf("%d\n",Class##84);
      //printf("%d\n",Class84);
      return 0;
}



