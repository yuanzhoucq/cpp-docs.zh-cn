---
title: "C 枚举声明 | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "#define 指令, 替代"
  - "声明, 枚举"
  - "声明枚举"
  - "定义指令 (#define), 替代"
  - "枚举数, 声明"
  - "命名常量, 枚举声明"
ms.assetid: bd18f673-4dda-4bc1-92fd-d1ce10074910
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C 枚举声明
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

枚举由一组命名整数常量构成。  枚举类型声明提供（可选）枚举标记的名称，并定义命名整数标识符集（称为“枚举集”、“枚举器常量”、“枚举器”或“成员”）。  具有枚举类型的变量存储该类型所定义的枚举集的值之一。  
  
 `enum` 类型的变量可用于索引表达式中，并且可用作所有算术和关系运算符的操作数。  枚举提供了 `#define` 预处理器指令的替代方法，带来的好处是可为您生成值并遵循一般范围规则。  
  
 在 ANSI C 中，定义枚举器常量值的表达式始终具有 `int` 类型；因此，与枚举变量关联的存储是单个 `int` 值所需的存储。  可以在 C 语言允许整数表达式的任意位置使用枚举常量或枚举类型的值。  
  
## 语法  
 *enum\-specifier*:  
 **enum**  *identifier*  opt **{** *enumerator\-list* **}**  
  
 **enum**  *identifier*  
  
 可选的 *identifier* 命名由 *enumerator\-list* 定义的枚举类型。  此标识符通常称为列表指定的枚举的“标记”。  该形式的类型说明符  
  
```  
  
enum identifier { enumerator-list }  
```  
  
 将 *identifier* 声明为由 *enumerator\-list* 非终止符指定的枚举的标记。  *enumerator\-list* 定义“枚举器内容”。下面详细介绍了 *enumerator\-list*。  
  
 如果标记的声明可见，则后续使用标记但忽略 *enumerator\-list* 的声明将指定之前声明的枚举的类型。  标记必须引用定义的枚举类型，并且该枚举类型必须在当前范围内。  由于在其他位置定义枚举类型，因此 *enumerator\-list* 不会出现在此声明中。  在定义枚举类型之前，派生自枚举类型的枚举和 `typedef` 声明的类型的声明可以使用枚举标记。  
  
## 语法  
 *enumerator\-list*:  
 *enumerator*  
  
 *enumerator\-list* **,**  `enumerator`  
  
 `enumerator`:  
 *enumeration\-constant*  
  
 *enumeration\-constant*  **\=**  *constant\-expression*  
  
 *enumeration\-constant*:  
 *identifier*  
  
 *enumeration\-list* 中的每个 *enumeration\-constant* 命名一个枚举集的值。  默认情况下，第一个 *enumeration\-constant* 与值 0 相关联。  列表中的下一个 *enumeration\-constant* 与 \(*constant\-expression* \+ 1\) 的值相关联，除非您显式将其与另一个值相关联。  *enumeration\-constant* 的名称与其值等效。  
  
 可以使用 *enumeration\-constant \= constant\-expression* 重写值的默认序列。  因此，如果 *enumeration\-constant \= constant\-expression* 出现在 *enumerator\-list* 中，则将 *enumeration\-constant* 与由 *constant\-expression* 给定的值相关联。  *constant\-expression* 必须具有 `int` 类型且可为负。  
  
 下面的规则适用于枚举集的成员：  
  
-   枚举集可以包含重复的常量值。  例如，可以将值 0 与两个不同的标识符关联，二者可能在同一集中命名为 `null` 和 `zero`。  
  
-   枚举列表中的标识符必须与同一范围中具有相同可见性的其他标识符不同，包括普通变量名和其他枚举列表中的标识符。  
  
-   枚举标记遵循一般范围规则。  它们必须不同于具有相同可见性的其他枚举、结构和联合标记。  
  
## 示例  
 这些示例阐释枚举声明：  
  
```  
enum DAY            /* Defines an enumeration type    */  
{  
    saturday,       /* Names day and declares a       */  
    sunday = 0,     /* variable named workday with    */   
    monday,         /* that type                      */  
    tuesday,  
    wednesday,      /* wednesday is associated with 3 */  
    thursday,  
    friday  
} workday;  
```  
  
 默认情况下，值 0 与 `saturday` 关联。  标识符 `sunday` 将显式设置为 0。  默认情况下，将为剩余标识符提供从 1 到 5 的值。  
  
 在此示例中，将集 `DAY` 中的值赋给变量 `today`。  
  
```  
enum DAY today = wednesday;  
```  
  
 请注意，可使用枚举常量的名称进行赋值。  由于之前声明了 `DAY` 枚举类型，因此仅枚举标记 `DAY` 是必需的。  
  
 若要显式将整数值赋给枚举数据类型的变量，请使用类型转换：  
  
```  
workday = ( enum DAY ) ( day_value - 1 );  
```  
  
 建议在 C 中进行此转换，但它不是必需的。  
  
```  
enum BOOLEAN  /* Declares an enumeration data type called BOOLEAN */  
{  
    false,     /* false = 0, true = 1 */  
    true   
};   
  
enum BOOLEAN end_flag, match_flag; /* Two variables of type BOOLEAN */  
```  
  
 还可将此声明指定为  
  
```  
enum BOOLEAN { false, true } end_flag, match_flag;\  
```  
  
 或指定为  
  
```  
enum BOOLEAN { false, true } end_flag;  
enum BOOLEAN match_flag;  
```  
  
 使用上述变量的示例可能类似于以下内容：  
  
```  
if ( match_flag == false )  
    {  
     .  
     .   /* statement */   
     .  
    }  
    end_flag = true;  
```  
  
 还可以声明未命名的枚举器数据类型。  忽略数据类型的名称，但可以声明变量。  变量 `response` 是已定义的类型的变量：  
  
```  
enum { yes, no } response;  
```  
  
## 请参阅  
 [枚举](../cpp/enumerations-cpp.md)