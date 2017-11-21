---
title: "构造函数初始化顺序中的更改 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: constructors, C++
ms.assetid: 8892c38d-6bf7-4cf7-ac8f-15e052135a79
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bdcfea2339bfe7aac93192e88a6ec39ce919c596
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="changes-in-constructor-initialization-order"></a>以构造函数初始化顺序进行更改
类构造函数初始化顺序已从托管扩展中的 c + + 更改为 Visual c + +。  
  
## <a name="comparison-of-constructor-initialization-order"></a>构造函数初始化顺序的比较  
 在 c + + 托管扩展中，构造函数初始化按下列顺序发生：  
  
1.  构造函数的基类，如果有的话，进行调用。  
  
2.  计算类的初始化列表。  
  
3.  执行类构造函数的代码体。  
  
 执行此顺序遵循相同的约定，如下所示本机 c + + 编程。 新的 Visual c + + 语言规定了 CLR 类的以下执行顺序：  
  
1.  计算类的初始化列表。  
  
2.  构造函数的基类，如果有的话，进行调用。  
  
3.  执行类构造函数的代码体。  
  
 请注意此更改仅适用于 CLR 类;Visual c + + 中的本机类仍遵循以前的约定。 在这两种情况下，这些规则将向上层叠整个的给定类的整个层次结构链。  
  
 请考虑下面的代码示例使用 c + + 托管扩展：  
  
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
  
 按照上述构造函数初始化顺序，我们应看到以下顺序执行时新的类的实例`B`构造：  
  
1.  基本类的构造函数`A`调用。 `_n`成员初始化为`1`。  
  
2.  类的初始化列表`B`计算。 `_m`成员初始化为`1`。  
  
3.  类的代码正文`B`执行。  
  
 现在考虑新的 Visual c + + 语法中相同的代码：  
  
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
  
 在将新的执行顺序类的实例`B`按照新构造语法是：  
  
1.  类的初始化列表`B`计算。 `_m`成员初始化为`0`(`0`是未初始化的值`_m`类成员)。  
  
2.  基本类的构造函数`A`调用。 `_n`成员初始化为`1`。  
  
3.  类的代码正文`B`执行。  
  
 请注意相似的语法生成相同的结果，这些代码示例。 类的构造函数`B`取决于基的类中的值`A`来初始化其成员。 但是，类的构造函数`A`尚未调用。 继承的类取决于基类构造函数中发生将内存或资源分配时，这种相关性会特别危险。  
  
## <a name="what-this-means-going-from-managed-extensions-for-c-to-visual-c-2010"></a>哪些这意味着从 Managed Extensions for c + + 转到 Visual c + + 2010年  
 在许多情况下基类，这些类还包含继承的类没有概念，所以应该是行为的透明的程序员对类的构造函数的执行顺序的更改。 但是，如以下代码示例所示，继承类的构造函数时可能会极大地影响其初始化列表取决于基类成员的值。 移动时你的代码从 Managed Extensions for c + + 到新的语法，考虑将这类构造移动到的类构造函数，正文其中保证执行上一次发生。  
  
## <a name="see-also"></a>另请参阅  
 [托管类型 (C + + /cli CL)](../dotnet/managed-types-cpp-cl.md)   
 [构造函数](../cpp/constructors-cpp.md)   
 