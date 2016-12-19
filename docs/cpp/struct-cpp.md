---
title: "struct (C++) | Microsoft Docs"
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
  - "struct"
  - "struct_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "结构构造函数"
ms.assetid: 3c6ba273-e248-4ff1-8c69-d2abcf1263c6
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# struct (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`struct` 关键字定义结构类型和\/或结构类型的变量。  
  
## 语法  
  
```  
[template-spec] struct [ms-decl-spec] [tag [: base-list ]]  
{   
   member-list   
} [declarators];  
[struct] tag declarators;  
```  
  
#### 参数  
 `template-spec`  
 可选模板规范。  有关详细信息，请参阅[模板规范](../Topic/Template%20Specifications.md)。  
  
 `struct`  
 `struct` 关键字。  
  
 `ms-decl-spec`  
 可选存储类规范。  有关详细信息，请参阅 [\_\_declspec](../cpp/declspec.md) 关键字。  
  
 `tag`  
 为结构提供的类型名称。  标记将变成结构范围内的保留字。  标记是可选项。  如果省略，则定义匿名结构。  有关详细信息，请参阅[匿名类类型](../cpp/anonymous-class-types.md)。  
  
 `base-list`  
 此结构将从中派生其成员的类或结构的可选列表。  有关详细信息，请参阅[基类](../cpp/base-classes.md)。  每个基类或结构名称的前面可具有访问说明符（[public](../cpp/public-cpp.md)、 [private](../cpp/private-cpp.md)、[protected](../cpp/protected-cpp.md)）和 [virtual](../cpp/virtual-cpp.md) 关键字。  有关详细信息，请参阅[控制对类成员的访问](../misc/controlling-access-to-class-members.md)中的成员访问表。  
  
 `member-list`  
 结构成员列表。  有关详细信息，请参阅[类成员概述](../cpp/class-member-overview.md)。  此处的唯一差异在于，使用 `struct` 代替了 `class`。  
  
 `declarators`  
 指定类名称的声明符列表。  声明符列表声明了一个或多个结构类型实例。  如果类的所有数据成员是 `public`，则声明符可以包含初始值设定项列表。  初始值设定项列表在结构中很常见，因为数据成员默认为 `public`。有关详细信息，请参阅[声明符概述](../cpp/overview-of-declarators.md)。  
  
## 备注  
 结构类型是用户定义的复合类型。  它由可具有不同类型的字段或成员构成。  
  
 在 C\+\+ 中，结构与类相同，只不过其成员默认为 `public`。  
  
 有关托管类和结构的信息，请参阅[类和结构](../windows/classes-and-structs-cpp-component-extensions.md)。  
  
## 使用结构  
 在 C 中，你必须显式使用 `struct` 关键字来声明结构。  在 C\+\+ 中，你不需要在定义该类型之后使用 `struct` 关键字。  
  
 可以选择在定义结构类型时，通过在右大括号和分号之间放置一个或多个逗号分隔的变量名称来声明变量。  
  
 可以初始化结构变量。  每个变量的初始化必须括在大括号中。  
  
 有关相关信息，请参阅 [class](../cpp/class-cpp.md)、[union](../cpp/unions.md) 和 [enum](../cpp/enumerations-cpp.md)。  
  
## 示例  
  
```  
#include <iostream>  
using namespace std;  
  
struct PERSON {   // Declare PERSON struct type  
    int age;   // Declare member types  
    long ss;  
    float weight;  
    char name[25];  
} family_member;   // Define object of type PERSON  
  
struct CELL {   // Declare CELL bit field  
    unsigned short character  : 8;  // 00000000 ????????  
    unsigned short foreground : 3;  // 00000??? 00000000  
    unsigned short intensity  : 1;  // 0000?000 00000000  
    unsigned short background : 3;  // 0???0000 00000000  
    unsigned short blink      : 1;  // ?0000000 00000000  
} screen[25][80];       // Array of bit fields   
  
int main() {  
    struct PERSON sister;   // C style structure declaration  
    PERSON brother;   // C++ style structure declaration  
    sister.age = 13;   // assign values to members  
    brother.age = 7;  
    cout << "sister.age = " << sister.age << '\n';  
    cout << "brother.age = " << brother.age << '\n';  
  
    CELL my_cell;  
    my_cell.character = 1;  
    cout << "my_cell.character = " << my_cell.character;  
}  
// Output:  
// sister.age = 13  
// brother.age = 7  
// my_cell.character = 1  
```  
  
## 请参阅  
 [定义类类型](http://msdn.microsoft.com/zh-cn/e8c65425-0f3a-4dca-afc2-418c3b1e57da)