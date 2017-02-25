---
title: "以构造函数初始化顺序进行更改 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "构造函数, C++"
ms.assetid: 8892c38d-6bf7-4cf7-ac8f-15e052135a79
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 以构造函数初始化顺序进行更改
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 C\+\+ 托管到 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]，类构造函数的初始化顺序已经发生变化。  
  
## 构造函数初始化顺序的比较  
 在 C\+\+ 托管扩展中，构造函数的初始化是按以下顺序进行的：  
  
1.  如果存在基类的构造函数则调用该构造函数。  
  
2.  计算该类的初始化列表。  
  
3.  执行类构造函数的代码正文。  
  
 此执行顺序与本机 C\+\+ 编程遵守相同的约定。  新 Visual C\+\+ 语言规定了 CLR 类的执行顺序，如下所示：  
  
1.  计算该类的初始化列表。  
  
2.  如果存在基类的构造函数则调用该构造函数。  
  
3.  执行类构造函数的代码正文。  
  
 请注意，此更改仅适用于 CLR 类，[!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 中的本机类仍遵守以前的约定。  在这两种情况下，这些规则将向上层叠，贯穿给定类的整个层次结构链。  
  
 请考虑以下使用 C\+\+ 托管扩展的代码示例：  
  
```  
__gc class A  
{  
public:  
   A() : _n(1)  
   {  
   }  
  
protected:  
   int _n;  
};  
  
__gc class B : public A  
{  
public:  
   B() : _m(_n)  
   {  
   }  
private:  
   int _m;  
};  
```  
  
 按照上述的构函数初始化顺序，在构造类 `B` 的新实例，我们应看到如下的执行顺序：  
  
1.  调用基类 `A` 的构造函数。  将 `_n` 成员初始化为 `1`。  
  
2.  计算类 `B` 的初始化列表。  将 `_m` 成员初始化为 `1`。  
  
3.  执行类 `B` 的代码正文。  
  
 现在请考虑以新 Visual C\+\+ 语法表示的相同代码：  
  
```  
ref class A  
{  
public:  
   A() : _n(1)  
   {  
   }  
  
protected:  
   int _n;  
};  
  
ref class B : A  
{  
public:  
   B() : _m(_n)  
   {  
   }  
private:  
   int _m;  
};  
```  
  
 按照新语法构造的类 `B` 的新实例的执行顺序如下：  
  
1.  计算类 `B` 的初始化列表。  将 `_m` 成员初始化为 `0`（`0` 是 `_m` 类成员的未初始化值）。  
  
2.  调用基类 `A` 的构造函数。  将 `_n` 成员初始化为 `1`。  
  
3.  执行类 `B` 的代码正文。  
  
 请注意，对于这些代码示例，相似的语法产生了不同的结果。  类 `B` 的构造函数依赖于基类 `A` 的值来初始化其成员。  但并未调用类 `A` 的构造函数。  如果需要分配内存或资源才能在基类构造函数中生成继承类，则此种依赖关系将是非常危险的。  
  
## 从 C\+\+ 托管扩展到 Visual C\+\+ 2010 意味着什么  
 在许多情况下，对类构造函数执行顺序的更改应对程序员透明，因为基类不了解继承类的行为。  但是，如这些代码示例所阐释的，如果继承类的初始化列表依赖于来自基类成员的值，则继承类的构造函数将受到很大影响。  在将 C\+\+ 托管扩展代码转换为使用新的语法时，请考虑将这种构造移到类构造函数体内，在这里，可保证这种构造在最后执行。  
  
## 请参阅  
 [托管类型 \(C\+\+\/CL\)](../dotnet/managed-types-cpp-cl.md)   
 [构造函数](../cpp/constructors-cpp.md)   
 [构造函数初始值设定项](../misc/constructor-initializers.md)