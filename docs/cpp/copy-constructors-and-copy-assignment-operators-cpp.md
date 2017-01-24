---
title: "复制构造函数和复制赋值运算符 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "= 运算符, 复制对象"
  - "赋值到复制对象"
  - "赋值运算符, 用于复制对象"
  - "赋值语句, 复制对象"
  - "复制对象"
  - "初始化对象, 通过复制对象"
  - "对象 [C++], 复制"
ms.assetid: a94fe1f9-0289-4fb9-8633-77c654002c0d
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 复制构造函数和复制赋值运算符 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  从 C\+\+ 11 中开始，该语言支持两种类型的分配：*复制赋值*和*移动赋值*。  在本文中，“赋值”意味着复制赋值，除非有其他显式声明。  有关移动分配的信息，请参阅[移动构造函数和移动赋值运算符 \(C\+\+\)](http://msdn.microsoft.com/zh-cn/1442de5f-37a5-42a1-83a6-ec9cfe0414db)。  
>   
>  赋值操作和初始化操作都会导致对象被复制。  
  
-   **赋值**：在将一个对象的值赋给另一个对象时，第一个对象将复制到第二个对象中。  因此，  
  
    ```cpp  
    Point a, b;  
    ...  
    a = b;  
    ```  
  
     导致 `b` 的值被复制到 `a` 中。  
  
-   **初始化**：在以下情况下将进行初始化：声明新对象、参数通过值传递给函数或值通过值从函数返回。  
  
 您可以为类类型的对象定义“复制”的语义。  例如，考虑此代码：  
  
```cpp  
TextFile a, b;  
a.Open( "FILE1.DAT" );  
b.Open( "FILE2.DAT" );  
b = a;  
```  
  
 前面的代码可能表示“将 FILE1.DAT 的内容复制到 FILE2.DAT”，也可能表示“忽略 FILE2.DAT 并使 `b` 成为 FILE1.DAT 的另一个句柄”。 您必须将适当的复制语义附加到每个类，如下所示。  
  
-   通过将赋值运算符 `operator=` 与对类类型的引用一起用作返回类型和 `const` 引用所传递的参数（例如，`ClassName& operator=(const ClassName& x);`）。  
  
-   通过通过复制构造函数。  有关复制构造函数的详细信息，请参阅[声明构造函数的规则](../misc/rules-for-declaring-constructors.md)。  
  
 如果不声明复制构造函数，编译器将为你生成 member\-wise 复制构造函数。  如果不声明复制赋值运算符，编译器将为你生成 member\-wise 复制赋值运算符。 声明复制构造函数不会取消编译器生成的复制赋值运算符，反之亦然。  如果实现上述其中一项，建议您还实现另一项以使代码的含义变得明确。  
  
 [\(NOTINBUILD\) Memberwise Assignment and Initialization](http://msdn.microsoft.com/zh-cn/94048213-8b49-4416-8069-b1b7a6f271f9)中更详细地介绍了逐个成员赋值。  
  
 复制构造函数采用了 *class\-name***&** 类型的参数，其中 *class\-name* 是为其定义构造函数的类的名称。  例如:  
  
```cpp  
// spec1_copying_class_objects.cpp  
class Window  
{  
public:  
    Window( const Window& ); // Declare copy constructor.  
    // ...  
};  
  
int main()  
{  
}  
```  
  
> [!NOTE]
>  尽可能创建该类型的复制构造函数的参数 *const class\-name***&**。  这可防止复制构造函数意外更改从中复制它的对象。  它还支持从 **const** 对象进行复制。  
  
## 编译器生成的构造函数  
 编译器生成的复制构造函数（如用户定义的复制构造函数）具有单个参数类型“对 *class\-name* 的引用”。 当所有基类和成员类都具有声明为采用 **const** *class\-name***&** 类型的单个参数的复制构造函数时，将引发异常。  在这种情况下，编译器生成的复制构造函数的参数也是 **const**。  
  
 当复制构造函数的参数类型不是 **const** 时，通过复制 **const** 对象进行初始化将产生错误。  反之则不然：如果参数是 **const**，您可以通过复制不是 **const** 的对象进行初始化。  
  
 编译器生成的赋值运算符遵循关于 **const** 的相同模式。 除非所有基类和成员类中的赋值运算符都采用 **const** *class\-name&* 类型的参数，否则它们将采用 *class\-name***&** 类型的单个参数。 在这种情况下，类的生成的赋值运算符采用 **const** 参数。  
  
> [!NOTE]
>  当虚拟基类由复制构造函数（编译器生成或用户定义的）初始化时，将只初始化这些基类一次：在构造它们时。  
  
 含义类似于复制构造函数的含义。  当参数类型不是 **const** 时，从 **const** 对象赋值将产生错误。  反之则不然：如果将 **const** 值赋给不是 **const** 的值，则赋值能成功。  
  
 有关重载赋值运算符的详细信息，请参阅[赋值](../cpp/assignment.md)。  
  
## 请参阅  
 [特殊成员函数](../misc/special-member-functions-cpp.md)