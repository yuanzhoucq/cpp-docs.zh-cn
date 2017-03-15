---
title: "编译器警告（等级 4）C4512 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4512"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4512"
ms.assetid: afb68995-684a-4be5-a73a-38d7a16dc030
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# 编译器警告（等级 4）C4512
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“类”：无法生成赋值运算符  
  
 编译器无法为给定的类生成赋值运算符。  未创建任何赋值运算符。  
  
 派生类不可访问的基类的赋值运算符可导致此警告。  
  
 若要避免此警告，请为类指定用户定义的赋值运算符。  
  
 编译器还会为不会定义此函数的类生成一个赋值运算符函数。  此赋值运算符是对象的数据成员的成员复制。  因为无法在初始化之后修改 `const` 数据项，所以如果类包含 `const` 项，则默认赋值运算符将不起作用。  出现C4512 警告的另一个原因是声明了引用类型的非静态数据成员。  如果这样做是为了创建一个非可复制的类型，则还必须防止创建默认复制构造函数。  
  
 可使用以下三种方式之一解决代码的 C4512 警告：  
  
-   显式定义类的赋值运算符。  
  
-   删除来自类中数据项的**常量**或引用运算符。  
  
-   使用 \#pragma [警告](../../preprocessor/warning.md)语句来禁止显示警告。  
  
## 示例  
 以下示例生成 C4512。  
  
```  
// C4512.cpp  
// compile with: /EHsc /W4  
// processor: x86  
  
class Base {  
private:  
   const int a;  
  
public:  
   Base(int val = 0) : a(val) {}  
   int get_a() { return a; }  
};   // C4512 warning  
  
class Base2 {  
private:  
   const int a;  
  
public:  
   Base2(int val = 0) : a(val) {}  
   Base2 & operator=( const Base2 & ) { return *this; }  
   int get_a() { return a; }  
};  
  
// Type designer intends this to be non-copyable because it has a   
// reference member  
class Base3  
{  
private:  
   char& cr;  
  
public:  
   Base3(char& r) : cr(r) {}  
   // Uncomment the following line to explicitly disable copying:  
   // Base3(const Base3&) = delete;   
};   // C4512 warning  
  
int main() {  
   Base first;  
   Base second;  
  
   // OK  
   Base2 first2;  
   Base2 second2;  
  
   char c = 'x';  
   Base3 first3(c);  
   Base3 second3 = first3; // C2280 if no default copy ctor  
}  
  
```