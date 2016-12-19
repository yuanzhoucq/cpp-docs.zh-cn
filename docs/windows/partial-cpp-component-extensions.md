---
title: "部分（C++ 组件扩展） | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "partial_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "partial — 部分"
  - "C++/CX, 部分"
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 部分（C++ 组件扩展）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`partial` 关键字使同一 ref 类的不同部分可独立授权并位于不同的文件中。  
  
## 所有运行时  
 \(此语言功能仅适用于 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]。\)  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 对于具有两个分部定义的 ref 类，`partial` 关键字在该定义首次出现时使用，并且通常由自动生成的代码完成，因此人工代码编写者就不会非常频繁地使用关键字。  对于类的所有后续分部定义，请省略来自*类键*关键字和类标识符的`partial`修饰符。  当编译器遇到以前已定义的 ref 类和类标识符，但无 `partial` 关键字时，它会在内部将 ref 类定义的所有部分合并为一个定义。  
  
### 语法  
  
```cpp  
  
partial class-key identifier {  
   /* The first part of the partial class definition. This is typically auto-generated*/  
}  
// ...  
class-key identifier {  
   /* The subsequent part(s) of the class definition. The same identifier is specified, but the "partial" keyword is omitted. */  
}  
  
```  
  
### 参数  
 *class\-key*  
 声明由 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 支持的类或结构的关键字。  `ref class`、`value class`、`ref struct` 或 `value struct`。  
  
 *identifier*  
 已定义类型的名称。  
  
### 备注  
 分部类是支持不同方案，在这些情方案中，您在一个文件中修改一部分类定义，而自动代码生成软件（例如 XAML 设计器）在另一文件中修改同一类中的代码。  通过使用分部类，可以防止自动代码生成器重写代码。  在 Visual Studio 项目中，`partial` 修饰符自动应用于生成的文件。  
  
 内容：由于具有两个异常，如果 `partial` 关键字省略，则分部类定义可包含全部类定义所包含的所有内容。  但是，您不能指定类可访问性（例如，`public partial class X {…};`{…};），或者 `declspec`。  
  
 用于对*标识符identifier*进行部分类定义的访问说明符，不会影响对标识符*identifier*进行后续部分类或完整类定义的默认辅助功能。  允许静态数据成员的内联定义。  
  
 声明：类的分部定义*标识符identifier*只引入*identifier标识符*名称标识符，但是*identifier*不能以要求类定义的方式使用。  在编译器遇到*identifier*标识符的完整定义之前，名称*标识符identifier*不能用于表示标识符*identifier*的大小，或者用于使用 *标识符identifier* 的基像或成员。  
  
 数字和顺序：*标识符identifier*可以有零个或多个分布类定义存在。  *标识符identifier*的每个分类定义必须在词法上优先于*标识符identifier*的完整定义（如果具有完整定义；除非已前向声明，否则类不可用），但是不需要优先于*identifier标识符*的前向声明。  所有类键必须匹配。  
  
 完整定义：在类*标识符identifier*的完整定义点，行为是相同的，就好像*identifier标识符*的定义已按照在分部类中遇到和定义基类、成员等的顺序，声明了所有这些基类、成员等一样。  
  
 模板：分部类不能作为模板。  
  
 泛型：如果完整定义是泛型，则分布类可以是泛型。  但是每个部分和完整类必须具有相同的泛型参数，包括形参名。  
  
 有关如何使用 `partial` 关键字的更多信息，请 [分部类 \(C\+\+\/CX\)](http://go.microsoft.com/fwlink/p/?LinkId=249023)参见。  
  
### 要求  
 编译器选项：**\/ZW**  
  
## 公共语言运行时  
 \(此语言功能不适用于公共语言运行时。\)  
  
## 请参阅  
 [分部类 \(C\+\+\/CX\)](http://go.microsoft.com/fwlink/p/?LinkId=249023)