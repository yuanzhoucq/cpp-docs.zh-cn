---
title: "结构 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- struct_cpp
dev_langs:
- C++
helpviewer_keywords:
- struct constructors
ms.assetid: 3c6ba273-e248-4ff1-8c69-d2abcf1263c6
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 4918adb779a620afd4a0c1e4ef64ef9892de1ba8
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="struct-c"></a>struct (C++)
`struct` 关键字定义结构类型和/或结构类型的变量。  
  
## <a name="syntax"></a>语法  
  
```  
[template-spec] struct[ms-decl-spec] [tag [: base-list ]]  
{   
   member-list   
} [declarators];  
[struct] tag declarators;  
```  
  
#### <a name="parameters"></a>参数  
 `template-spec`  
 可选模板规范。 有关详细信息，请参阅[模板规范](templates-cpp.md)。  
  
 `struct`  
 `struct` 关键字。  
  
 `ms-decl-spec`  
 可选存储类规范。 有关详细信息，请参阅[__declspec](../cpp/declspec.md)关键字。  
  
 `tag`  
 为结构提供的类型名称。 标记将变成结构范围内的保留字。 标记是可选项。 如果省略，则定义匿名结构。 有关详细信息，请参阅[匿名类类型](../cpp/anonymous-class-types.md)。  
  
 `base-list`  
 此结构将从中派生其成员的类或结构的可选列表。 请参阅[基类](../cpp/base-classes.md)有关详细信息。 每个基的类或结构名称的前面可具有访问说明符 ([公共](../cpp/public-cpp.md)，[私有](../cpp/private-cpp.md)，[保护](../cpp/protected-cpp.md)) 和[虚拟](../cpp/virtual-cpp.md)关键字。 请参阅中的成员访问表[控制对类成员的访问](member-access-control-cpp.md)有关详细信息。  
  
 `member-list`  
 结构成员列表。 请参阅[类成员概述](../cpp/class-member-overview.md)有关详细信息。 此处的唯一差异在于，使用 `struct` 代替了 `class`。  
  
 `declarators`  
 指定类名称的声明符列表。 声明符列表声明了一个或多个结构类型实例。 如果类的所有数据成员是 `public`，则声明符可以包含初始值设定项列表。 初始值设定项列表在结构中很常见，因为数据成员默认为 `public`。  请参阅[的声明符概述](../cpp/overview-of-declarators.md)有关详细信息。  
  
## <a name="remarks"></a>备注  
 结构类型是用户定义的复合类型。 它由可具有不同类型的字段或成员构成。  
  
 在 C++ 中，结构与类相同，只不过其成员默认为 `public`。  
  
 有关托管的类和结构的信息，请参阅[类和结构](../windows/classes-and-structs-cpp-component-extensions.md)。  
  
## <a name="using-a-structure"></a>使用结构  
 在 C 中，您必须显式使用 `struct` 关键字来声明结构。 在 C++ 中，你不需要在定义该类型之后使用 `struct` 关键字。  
  
 可以选择在定义结构类型时，通过在右大括号和分号之间放置一个或多个逗号分隔的变量名称来声明变量。  
  
 可以初始化结构变量。 每个变量的初始化必须括在大括号中。  
  
 有关相关信息，请参阅[类](../cpp/class-cpp.md)，[联合](../cpp/unions.md)，和[枚举](../cpp/enumerations-cpp.md)。  
  
## <a name="example"></a>示例  
  
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
  

