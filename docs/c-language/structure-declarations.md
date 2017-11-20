---
title: "结构声明 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- structure declarations
- anonymous structures
- types [C], declarations
- structure members
- embedded structures
ms.assetid: 5be3be77-a236-4153-b574-7aa77675df7f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c91c3834b5a4647f7c9cd41820dc04e5597277f0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="structure-declarations"></a>结构声明
“结构声明”用于为类型命名和指定一系列可具有不同类型的变量值（称为结构的“成员”或“字段”）。 可选标识符（称为“标记”）为结构类型命名并可用于结构类型的后续引用。 该结构类型的变量保留该类型定义的整个序列。 C 中的结构类似于其他语言中称为“记录”的类型。  
  
## <a name="syntax"></a>语法  
 *struct-or-union-specifier*:  
 *struct-or-union identifier* opt**{** *struct-declaration-list* **}**  
  
 *struct-or-union identifier*  
  
 *struct-or-union*:  
 **struct**  
  
 **union**  
  
 *struct-declaration-list*:  
 *struct-declaration*  
  
 *struct-declaration-list struct-declaration*  
  
 结构内容定义为  
  
 *struct-declaration*:  
 *specifier-qualifier-list struct-declarator-list*  **;**  
  
 *specifier-qualifier-list*:  
 *type-specifier specifier-qualifier-list* opt  
  
 *type-qualifier specifier-qualifier-list* opt  
  
 *struct-declarator-list*:  
 *struct-declarator*  
  
 *struct-declarator-list*  **,**  *struct-declarator*  
  
 *struct-declarator*:  
 `declarator`  
  
 结构类型的声明不为结构预留空间。 它只是结构变量的最新声明的模板。  
  
 前面定义的 *identifier*（标记）可用于引用在其他位置定义的结构类型。 在本例中，只要该定义可见，*struct-declaration-list* 就不能重复。 在定义结构类型之前，指向结构类型的结构和 typedef 的指针的声明可使用结构标记。 但是，在实际使用字段大小之前，一定会先遇到结构定义。 这是类型和类型标记的不完整定义。 为了完成此定义，类型定义之后必须出现在相同的范围中。  
  
 *struct-declaration-list* 指定结构成员的类型和名称。 *struct-declaration-list* 参数包含一个或多个变量或位域声明。  
  
 每个在 *struct-declaration-list* 中声明的变量都被定义为结构类型的成员。 *struct-declaration-list* 中的变量声明与本节中讨论的其他变量声明的形式相同，只不过声明不能包含存储类说明符或初始值设定项。 结构成员可具有除类型 `void`、不完整类型或函数类型之外的任何变量类型。  
  
 不能将成员声明为具有其出现的结构的类型。 但是，可将成员声明为指向结构类型（只要该结构类型具有标记，该成员就会出现在其中）的指针。 这使您可以创建结构的链接列表。  
  
 结构的范围与其他标识符的一样。 结构标识符必须不同于具有相同可见性的其他结构、联合和枚举标记。  
  
 *struct-declaration-list* 中的每个 *struct-declaration* 在列表中都必须是唯一的。 但是，*struct-declaration-list* 中的标识符名称不必与普通变量名称或其他结构声明列表中的标识符名称不同。  
  
 嵌套结构也可以访问，就像它们是在文件范围级别声明的一样。 例如，给定以下声明：  
  
```  
struct a  
{  
    int x;  
    struct b  
    {  
      int y;  
    } var2;  
} var1;  
```  
  
 以下两个声明都是合法的：  
  
```  
struct a var3;  
struct b var4;  
```  
  
## <a name="examples"></a>示例  
 以下示例演示了结构声明：  
  
```  
struct employee   /* Defines a structure variable named temp */  
{  
    char name[20];  
    int id;  
    long class;  
} temp;  
```  
  
 `employee` 结构有三个成员：`name`、`id` 和 `class`。 `name` 成员是一个包含 20 个元素的数组，`id` 和 `class` 分别为具有 `int` 和 **long** 类型的简单成员。 标识符 `employee` 是结构标识符。  
  
```  
struct employee student, faculty, staff;  
```  
  
 本示例定义了三个结构变量：`student`、`faculty` 和 `staff`。 每个结构都有相同的包含三个成员的列表。 成员被声明为具有在前面的示例中定义的结构类型 `employee`。  
  
```  
struct           /* Defines an anonymous struct and a */  
{                /* structure variable named complex  */  
    float x, y;  
} complex;  
```  
  
 `complex` 结构具有两个 **float** 类型的成员：`x` 和 `y`。 结构类型没有标记，因此是未命名或匿名的。  
  
```  
struct sample   /* Defines a structure named x */  
{  
    char c;  
    float *pf;  
    struct sample *next;  
} x;  
```  
  
 结构的前两个成员为 `char` 变量和指向 **float** 值的指针。 第三个成员 (`next`) 被声明为指向正在定义的结构类型 (`sample`) 的指针。  
  
 当不需要命名的标记时，匿名结构很有用。 当一个声明定义了所有结构实例时，就是这种情况。 例如：  
  
```  
struct  
{  
    int x;  
    int y;  
} mystruct;  
```  
  
 嵌入结构通常是匿名的。  
  
```  
struct somestruct  
{  
    struct    /* Anonymous structure */  
    {  
        int x, y;  
    } point;  
    int type;  
} w;  
```  
  
 **Microsoft 专用**  
  
 编译器允许未确定大小或零大小的数组作为结构的最后一个成员。 如果常量数组在不同的情况下大小不同，这可能很有用。 此类结构的声明类似于以下形式：  
  
 `struct` *identifier***{** *set-of-declarations* *type array-name***[ ];};**  
  
 未确定大小的数组仅在作为结构的最后一个成员时才出现。 只要所有封闭结构中都不再进一步声明成员，那么包含未确定大小的数组声明的结构就可以嵌入其他结构中。 不允许有此类结构的数组。 当应用于此类型的变量或应用于此类型本身时，`sizeof` 运算符假定数组的大小为 0。  
  
 如果结构声明是另一结构或联合的成员，则可以在没有声明符的情况下指定该结构声明。 字段名将提升到该封闭结构中。 例如，无名称结构类似于以下形式：  
  
```  
struct s  
{  
    float y;  
    struct  
    {  
        int a, b, c;  
    };  
    char str[10];  
} *p_s;  
.  
.  
.  
p_s->b = 100;  /* A reference to a field in the s structure */  
```  
  
 有关结构引用的信息，请参阅[结构和联合成员](../c-language/structure-and-union-members.md)。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [声明符和变量声明](../c-language/declarators-and-variable-declarations.md)