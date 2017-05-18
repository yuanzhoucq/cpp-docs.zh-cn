---
title: "编译器警告 （等级 4） C4471 |Microsoft 文档"
ms.custom: 
ms.date: 04/24/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4471
dev_langs:
- C++
helpviewer_keywords:
- C4471
ms.assetid: ccfd8bd5-bc1b-4be7-a6ea-0e3a7add6607
caps.latest.revision: 1
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: d7d097b399d3681ef523d8787ecc38af472840f6
ms.openlocfilehash: fc0ddb07ec768804be61185211bbac0ee6fbf2b6
ms.contentlocale: zh-cn
ms.lasthandoff: 04/28/2017

---
# <a name="compiler-warning-level-4-c4471"></a>编译器警告 （等级 4） C4471
*枚举*︰ 未区分范围的枚举的前向声明必须具有基础类型 (假定为 int)  
  
未区分范围的枚举的前向声明找的基础类型不带说明符。 默认情况下，Visual c + + 假定`int`是枚举的基础类型。 如果使用不同类型是在枚举定义中，例如，如果指定了不同的显式类型，或不同的类型隐式设置初始值设定项，这会导致问题。 您可能还必须可移植性问题;其他编译器不会假定`int`是枚举的基础类型。  
  
默认情况下; 此警告处于关闭状态你可以使用 /Wall 或 /w*N*4471 启用命令行上或使用 #pragma[警告](../../preprocessor/warning.md)源文件中。  
  
在某些情况下，此警告是虚假。 如果枚举的前向声明出现在定义之后，可能会触发此警告。 例如，此代码是有效，即使它可能会导致 C4471:  
  
```cpp  
// C4471a.cpp
// Compile with: cl /c /w14471 C4471a.cpp
enum Example { item = 0x80000000UL };
enum Example;    // Spurious C4471
// ...
```  
  
## <a name="example"></a>示例  
通常情况下，它是安全的完整定义用于未区分范围而不是前向声明枚举。 你可以将定义放入标头文件，并将其包含在引用它的源文件中。 这适用于 C + + 98 及更高版本编写的代码。 我们建议为可移植性和便于维护此解决方案。  
  
```cpp  
// C4471b.cpp
// Compile with: cl /c /w14471 C4471b.cpp
enum Example;    // C4471
// To fix, replace the line above with the enumeration definition:
// enum Example { item = 0x80000000UL };
// ...
```  
  
## <a name="example"></a>示例  
在 C + + 11 中，你可以添加显式类型，对未区分范围的枚举和其前向声明。 仅当复杂的标头包含逻辑禁止使用而不是前向声明的定义，我们建议此解决方案。 此解决方案可能会导致了维护问题︰ 如果更改用于枚举定义的基础类型，则还必须更改所有前向声明以匹配，或可能在你代码中有无提示的错误。 可以将前向声明放入标头文件，以尽量减少此问题。  
  
```cpp  
// C4471c.cpp
// Client code for enumeration defined in C4471d.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example;    // C4471, int assumed
// To fix, replace the lines above with the forward declarations:
// enum Example : unsigned;
// ...
```  
  
```cpp  
// C4471d.cpp
// Definition for enumeration used in C4471c.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example : unsigned { item = 0x80000000 }; // explicit type
// ...
```  
  
如果指定显式类型枚举，我们建议你还启用警告[C4369](compiler-warning-level-1-C4369.md)，这是在默认情况下。 这标识用例的枚举项要求与显式指定类型的类型不同的位置。
  
## <a name="example"></a>示例  
你可以更改代码以使用的范围的枚举，C + + 11 中的新增功能。 定义和使用枚举类型的任何客户端代码必须更改为使用的范围的枚举。 我们建议你使用的范围的枚举如果你有问题的命名空间污染，如定义的枚举项的名称仅限于枚举的作用域。 其他功能的范围枚举是其成员不能隐式转换为另一个整型或枚举类型，可以是一个细微的错误的来源。

```cpp  
// C4471e.cpp
// Client code for scoped enumeration defined in C4471f.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum Example;    // C4471
// To fix, replace the line above with the forward declaration:
// enum class Example;
// ...
```  
  
```cpp  
// C4471f.cpp
// Definition for scoped enumeration used in C4471e.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum class Example { item = 0 };
// ...
```  
  

