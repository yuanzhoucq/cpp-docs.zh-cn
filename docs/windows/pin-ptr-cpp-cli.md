---
title: "pin_ptr (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "pin_ptr_cpp"
  - "stdcli::language::pin_ptr"
  - "pin_ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pin_ptr 关键字 [C++]"
  - "钉住指针"
ms.assetid: 6c2e6c73-4ec2-4dce-8e1f-ccf3a9f9d0aa
caps.latest.revision: 28
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# pin_ptr (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

声明 *钉住指针*，仅使用在公共语言运行时。  
  
## 所有运行时  
 （无适用于所有运行时的语言功能的备注。）  
  
## Windows Runtime — Windows 运行时  
 \(此功能在 Windows 语言运行时不受支持。\)  
  
## 公共语言运行时  
 一个 *钉住指针* 是防止您的对象移动将在垃圾回收堆的内部指针。  也就是说钉住指针的值不是由公共语言运行时更改。  当向非托管函数传递托管类的地址时，这很有用，因为在解析非托管函数调用的过程中，该地址不会意外更改。  
  
### 语法  
  
```cpp  
[cli::]pin_ptr<cv_qualifier type> var = &initializer;  
```  
  
### 参数  
 *cv\_qualifier*  
 `const` 或 `volatile` 限定符。  默认情况下，钉住指针是 `volatile`。  为冗余，而不是错误声明钉住指针 `volatile`。  
  
 *type*  
 `initializer` 的类型。  
  
 *var*  
 `pin_ptr` 变量的名称。  
  
 *initializer*  
 引用类型元素，托管数组，或者任何其他的成员可以分配给本机指针的对象。  
  
### 备注  
 `pin_ptr` 表示本机指针的功能扩展。  因此，可以分配给本机指针的任何也可以分配给 `pin_ptr`。  内部指针允许运行同一组操作与本机指针，其中包括比较和指针算法。  
  
 托管类的对象或子对象可以固定，在垃圾回收过程情况下公共语言运行时不会移动。  使用此的基本用法是传递指向托管数据为托管函数调用的一个实参。  在回收周期期间，运行时将检查创建的元数据。因此不移动指向的钉住指针的项。  
  
 固定对象还固定字段；其值即或基元值类型字段。  但是，声明的字段跟踪句柄 \(`%`\) 不使用锁定。  
  
 固定在宿主的对象定义的子对象的固定整个对象的效果。  
  
 如果固定指针重新分配到新值，以前的实例指向不再将该表视为锁定。  
  
 对象固定，仅当它的 `pin_ptr` 指向它。  对象不再被锁定，则其固定指针超出范围，或者设置为 [nullptr](../windows/nullptr-cpp-component-extensions.md)。  在 `pin_ptr` 超出范围之后，固定对象在堆可以移动被垃圾回收器回收。  仍然指向对象的任何本机指针不会更新，并间接引用其中一个可能引发一不可恢复的异常。  
  
 如果对对象的固定指针 \(指向所有钉住指针超出了范围，重新分配到其他对象的点或分配 [nullptr](../windows/nullptr-cpp-component-extensions.md)\)，不保证对象不锁定。  
  
 钉住指针可以指向句柄引用、值类型或装箱类型的托管类型的句柄、成员或托管数组的元素。  它不能指向引用类型。  
  
 将指向本机 `pin_ptr` 对象的地址导致未定义的行为。  
  
 钉住指针只能声明作为堆栈上的非静态局部变量。  
  
 无法使用钉住指针所示：  
  
-   函数参数  
  
-   作为函数的返回类型。  
  
-   类成员的声明  
  
-   目标的类型约束。  
  
 `pin_ptr` 是`cli`命名空间中的类型。  有关详细信息，请参阅[Platform、default 和 cli 命名空间](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)。  
  
 有关智能指针的更多信息，请参见 [interior\_ptr \(C\+\+\/CLI\)](../windows/interior-ptr-cpp-cli.md)。  
  
 有关生成控制器的更多信息，请参阅[如何：钉住指针和数组](../windows/how-to-pin-pointers-and-arrays.md)和[如何：声明钉住指针和值类型](../windows/how-to-declare-pinning-pointers-and-value-types.md)。  
  
### 要求  
 编译器选项：**\/clr**  
  
### 示例  
 **示例**  
  
 下面的示例约束使用 `pin_ptr` 数组的第一个元素的位置。  
  
```  
// pin_ptr_1.cpp  
// compile with: /clr   
using namespace System;  
#define SIZE 10  
  
#pragma unmanaged  
// native function that initializes an array  
void native_function(int* p) {  
   for(int i = 0 ; i < 10 ; i++)  
    p[i] = i;  
}  
#pragma managed  
  
public ref class A {  
private:  
   array<int>^ arr;   // CLR integer array  
  
public:  
   A() {  
      arr = gcnew array<int>(SIZE);  
   }  
  
   void load() {  
   pin_ptr<int> p = &arr[0];   // pin pointer to first element in arr  
   int* np = p;   // pointer to the first element in arr  
   native_function(np);   // pass pointer to native function  
   }  
  
   int sum() {  
      int total = 0;  
      for (int i = 0 ; i < SIZE ; i++)  
         total += arr[i];  
      return total;  
   }  
};  
  
int main() {  
   A^ a = gcnew A;  
   a->load();   // initialize managed array using the native function  
   Console::WriteLine(a->sum());  
}  
```  
  
 **Output**  
  
  **45** **示例**  
  
 下面的示例表示内部指针转换为钉住的指针，并且，类型为返回 address\-of 运算符 \(`&`\) 是内部指针，当操作数在托管堆时。  
  
```  
// pin_ptr_2.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct G {  
   G() : i(1) {}  
   int i;  
};  
  
ref struct H {  
   H() : j(2) {}  
   int j;  
};  
  
int main() {  
   G ^ g = gcnew G;   // g is a whole reference object pointer  
   H ^ h = gcnew H;  
  
   interior_ptr<int> l = &(g->i);   // l is interior pointer  
  
   pin_ptr<int> k = &(h->j);   // k is a pinning interior pointer  
  
   k = l;   // ok  
   Console::WriteLine(*k);  
};  
```  
  
 **Output**  
  
 **1** **示例**  
  
 下面的示例演示，钉住的指针转换为另一种类型。  
  
```  
// pin_ptr_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref class ManagedType {  
public:  
   int i;  
};  
  
int main() {  
   ManagedType ^mt = gcnew ManagedType;  
   pin_ptr< int > pt = &mt->i;  
   *pt = 8;  
   Console::WriteLine(mt->i);  
  
   char *pc = ( char* ) pt;  
   *pc = 255;  
   Console::WriteLine(mt->i);  
}  
```  
  
 **Output**  
  
 **8**   
**255**