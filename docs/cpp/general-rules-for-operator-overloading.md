---
title: "运算符重载的一般规则 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "运算符重载, 规则"
ms.assetid: eb2b3754-35f7-4832-b1da-c502893dc0c7
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 运算符重载的一般规则
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

以下规则约束如何实现重载运算符。  但是，这些规则不适用于 [new](../cpp/new-operator-cpp.md) 和 [delete](../cpp/delete-operator-cpp.md) 运算符，这两个运算符将单独介绍。  
  
-   不能定义新运算符，如 \*\*。  
  
-   将运算符应用于内置数据类型时，不能重新定义其含义。  
  
-   重载运算符必须是非静态类成员函数或全局函数。  需要访问私有或受保护的类成员的全局函数必须声明为该类的友元。  全局函数必须至少采用一个类类型或枚举类型的参数，或者作为对类类型或枚举类型的引用的参数。  例如：  
  
    ```  
    // rules_for_operator_overloading.cpp  
    class Point  
    {  
    public:  
        Point operator<( Point & );  // Declare a member operator   
                                     //  overload.  
        // Declare addition operators.  
        friend Point operator+( Point&, int );  
        friend Point operator+( int, Point& );  
    };  
  
    int main()  
    {  
    }  
    ```  
  
     前面的代码示例将小于运算符声明为成员函数；但是，加法运算符被声明为具有友元访问的全局函数。  请注意，可以为给定运算符提供多个实现。  对于前面的加法运算符，将提供两个实现以便于交换。  同样可能会实现用于将 `Point` 与 `Point` 相加、将 `int` 与 `Point` 相加等此类运算符。  
  
-   运算符遵循它们通常用于内置类型时指定的操作数的优先级、分组和数量。  因此，没有方法来表达概念“将 2 和 3 与 `Point` 类型的对象相加”（应该让 2 与 *x* 坐标相加，3 与 *y* 坐标相加）。  
  
-   声明为成员函数的一元运算符将不采用参数；如果声明为全局函数，它们将采用一个参数。  
  
-   声明为成员函数的二元运算符将采用一个参数；如果声明为全局函数，它们将采用两个参数。  
  
-   如果运算符可用作一元或二元运算符（**&**、**\***、**\+** 和 **\-**），则可以单独重载每个使用。  
  
-   重载运算符不能具有默认参数。  
  
-   除赋值 \(`operator=`\) 之外的所有重载运算符均由派生类继承。  
  
-   成员函数重载运算符的第一个参数始终属于针对其调用运算符的对象的类类型（从中声明运算符的类或派生自该类的类）。  没有为第一个参数提供转换。  
  
 请注意，任何运算符的含义都可以完全更改。  这包括 address\-of \(**&**\)、赋值 \(**\=**\) 和函数调用运算符的含义。  此外，还可以使用运算符重载来更改可用来确定内置类型的标识。  例如，以下四个语句在完全计算时通常是等效的：  
  
```  
var = var + 1;  
var += 1;  
var++;  
++var;  
```  
  
 无法依靠此标识来确定重载运算符的类类型。  此外，在使用这些运算符时针对基本类型的某些隐含要求对重载运算符放宽了。  例如，相加\/赋值运算符 `+=` 要求在应用于基本类型时左操作数是左值；在重载该运算符时，不存在这样的要求。  
  
> [!NOTE]
>  为保持一致性，定义重载运算符时通常最好遵循内置类型的模型。  如果某个重载运算符的语义与它在其他上下文中的含义差别很大，则它造成的混淆会盖过它的用处。  
  
## 请参阅  
 [运算符重载](../cpp/operator-overloading.md)