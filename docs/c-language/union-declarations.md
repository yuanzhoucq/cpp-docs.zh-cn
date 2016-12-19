---
title: "联合声明 | Microsoft Docs"
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
  - "union 关键字 [C], 声明"
  - "联合"
  - "可变记录"
ms.assetid: 978c6165-e0ae-4196-afa7-6d94e24f62f7
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 联合声明
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

“联合声明”指定一组变量值和（可选）一个命名联合的标记。  变量值称为联合的“成员”，并且可以具有不同的类型。  联合类似于其他语言中的“变体记录”。  
  
## 语法  
 *struct\-or\-union\-specifier*:  
 *struct\-or\-union identifier*  opt **{** *struct\-declaration\-list* **}**  
  
 *struct\-or\-union identifier*  
  
 *struct\-or\-union*:  
 **struct**  
  
 **union**  
  
 *struct\-declaration\-list*:  
 *struct\-declaration*  
  
 *struct\-declaration\-list struct\-declaration*  
  
 联合内容定义为  
  
 *struct\-declaration*:  
 *specifier\-qualifier\-list struct\-declarator\-list*  **;**  
  
 *specifier\-qualifier\-list*:  
 *type\-specifier specifier\-qualifier\-list*  opt  
  
 *type\-qualifier specifier\-qualifier\-list*  opt  
  
 *struct\-declarator\-list*:  
 *struct\-declarator*  
  
 *struct\-declarator\-list*  **,**  *struct\-declarator*  
  
 带 **union** 类型的变量存储该类型所定义的值之一。  相同的规则可控制结构和联合声明。  联合还可以具有位域。  
  
 联合的成员不能包含不完整类型、类型 `void` 或函数类型。  因此，成员不能是联合的实例，但可以是指向将声明的联合类型的指针。  
  
 联合类型声明只是一个模板。  不保留内存，直到声明变量。  
  
> [!NOTE]
>  如果声明两个类型的联合并存储一个值，但使用其它类型访问该联合，则结果是不可靠的。  例如，声明 **float** 和 `int` 的联合。  存储一个 **float** 值，但程序稍后会将该值作为 `int` 进行访问。  在这种情况下，值取决于 **float** 值的内部存储区。  整数值是不可靠的。  
  
## 示例  
 下面是联合的示例：  
  
```  
union sign   /* A definition and a declaration */  
{  
    int svar;  
    unsigned uvar;  
} number;  
```  
  
 此示例定义了带 `sign` 类型的联合变量，并声明了一个名为 `number` 的变量，该变量包含两个成员：`svar`（一个带符号整数）和 `uvar`（一个无符号整数）。  此声明允许将 `number` 的当前值存储为带符号的值或无符号的值。  与此联合类型关联的标记为 `sign`。  
  
```  
union               /* Defines a two-dimensional */  
{                   /*  array named screen */  
    struct      
    {   
      unsigned int icon : 8;    
      unsigned color : 4;  
    } window1;  
    int screenval;  
} screen[25][80];  
```  
  
 `screen` 数组包含 2,000 个元素。  数组的每个元素均为一个包含以下两个成员的联合：`window1` 和 `screenval`。  `window1` 成员是带两个位域成员（`icon` 和 `color`）的结构。  `screenval` 成员是一个 `int`。  在任意给定时间，每个联合元素保留由 `screenval` 表示的 `int` 或由 `window1` 表示的结构。  
  
 **Microsoft 专用**  
  
 如果嵌套的联合是另一个结构或联合的成员，则可以匿名声明嵌套的联合。  这是一个无名称联合的示例：  
  
```  
struct str  
{  
    int a, b;  
    union            / * Unnamed union */  
    {  
      char c[4];  
      long l;  
      float f;  
   };  
   char c_array[10];  
} my_str;  
.  
.  
.  
my_str.l == 0L;  /* A reference to a field in the my_str union */  
```  
  
 联合通常嵌套在一个结构中，该结构包含一个在任意特定时间给定联合中包含的数据类型的字段。  这是此类联合的声明的示例：  
  
```  
struct x  
{  
    int type_tag;  
    union  
    {  
      int x;  
      float y;  
    }  
}  
```  
  
 有关引用联合的信息，请参阅[结构和联合成员](../c-language/structure-and-union-members.md)。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [声明符和变量声明](../c-language/declarators-and-variable-declarations.md)