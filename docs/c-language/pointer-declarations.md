---
title: "指针声明 | Microsoft Docs"
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
  - "const 关键字 [C]"
  - "声明, 指针"
  - "指针声明"
  - "指针, 声明"
ms.assetid: 8b3b7fc7-f44d-480d-b6f9-cebe4e5462a6
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 指针声明
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

“指针声明”可命名指针变量并指定该变量所指向的对象的类型。  声明为指针的变量保留了一个内存地址。  
  
## 语法  
 `declarator`:  
 `pointer` opt *direct\-declarator*  
  
 *direct\-declarator*:  
 *identifier*  
  
 **\(**  *declarator*  **\)**  
  
 *direct\-declarator*  **\[**  *constant\-expression* opt **\]**  
  
 *direct\-declarator*  **\(**  *parameter\-type\-list*  **\)**  
  
 *direct\-declarator*  **\(**  *identifier\-list* opt **\)**  
  
 `pointer`:  
 **\*** *type\-qualifier\-list* opt  
  
 **\*** *type\-qualifier\-list* opt `pointer`  
  
 *type\-qualifier\-list*:  
 *type\-qualifier*  
  
 *type\-qualifier\-list type\-qualifier*  
  
 *type\-specifier* 用于指定对象的类型，可以是任何基本、结构或联合类型。  指针变量也可以指向函数、数组和其他指针。（有关声明和解释更复杂的指针类型的信息，请参阅[解释更复杂的声明符](../c-language/interpreting-more-complex-declarators.md)。）  
  
 通过将 *type\-specifier* 设为 `void`，您可以延迟指针引用的类型的规范。  这种项称为“指向 `void` 的指针”，作为 `void *` 写入。  声明为指向 `void` 的指针的变量可用于指向任意类型的对象。  但是，若要对指针或指针指向的对象执行大多数操作，则必须为每个操作显式指定指针指向的类型。（**char \*** 类型和 **void \*** 类型的变量不用类型强制转换即可赋值兼容。）此类转换可使用类型强制转换完成（有关详细信息，请参阅 [Type\-Cast 转换](../c-language/type-cast-conversions.md)）。  
  
 *type\-qualifier* 可以是 **const** 或 `volatile` 之一，也可以是这两者。  它们分别指定了程序本身无法修改的指针 \(**const**\)，或程序的控制之外的某些进程可以合理修改的指针 \(`volatile`\)。（有关 **const** 和 `volatile` 的详细信息，请参阅[类型限定符](../c-language/type-qualifiers.md)。）  
  
 `declarator` 可为变量命名，并可包含类型修饰符。  例如，如果 `declarator` 表示数组，则将指针的类型修改为指向数组的指针。  
  
 在定义结构、联合或枚举类型之前，您可以声明指向结构、联合或枚举类型的指针。  您可使用结构或联合标记声明指针，如下面的示例所示。  此类声明是允许的，因为编译器不需要知道要为指针变量分配空间的结构或联合的大小。  
  
## 示例  
 以下示例演示了指针声明。  
  
```  
char *message; /* Declares a pointer variable named message */  
```  
  
 `message` 指针指向具有 `char` 类型的变量。  
  
```  
int *pointers[10];  /* Declares an array of pointers */  
```  
  
 `pointers` 数组有 10 个元素；每个元素都是一个指向具有 `int` 类型的变量的指针。  
  
```  
int (*pointer)[10]; /* Declares a pointer to an array of 10 elements */  
```  
  
 指针变量指向具有 10 个元素的数组。  此数组中的每个元素都有 `int` 类型。  
  
```  
int const *x;      /* Declares a pointer variable, x,  
                      to a constant value */   
```  
  
 可以将指针 `x` 修改为指向不同的 `int` 值，但该指针指向的值无法修改。  
  
```  
const int some_object = 5 ;  
int other_object = 37;  
int *const y = &fixed_object;  
int volatile *const z = &some_object;  
int *const volatile w = &some_object;  
```  
  
 这些声明中的变量 `y` 被声明为指向 `int` 值的常量指针。  该指针指向的值可以修改，但指针本身必须始终指向同一位置：`fixed_object` 的地址。  同样，`z` 是常量指针，但它也被声明为指向值不能由程序修改的 `int`。  附加说明符 `volatile` 指示，尽管程序无法修改 `z` 所指向的 **const int** 的值，但当前与程序一起运行的进程可以合理地修改该值。  `w` 的声明指定，程序无法更改指向的值，并且程序无法修改指针。  
  
```  
struct list *next, *previous; /* Uses the tag for list */  
```  
  
 本示例声明了指向结构类型 `list` 的两个指针变量 `next` 和 `previous`。  只要 `list` 类型定义与声明具有相同的可见性，则此声明可以出现在 `list` 结构类型的定义前面（请参阅下一个示例）。  
  
```  
struct list   
{  
    char *token;  
    int count;  
    struct list *next;  
} line;  
```  
  
 变量 `line` 具有名为 `list` 的结构类型。  `list` 结构类型有三个成员：第一个成员是指向 `char` 值的指针，第二成员是 `int` 值，第三成员是指向另一个 `list` 结构的指针。  
  
```  
struct id   
{  
    unsigned int id_no;  
    struct name *pname;  
} record;  
```  
  
 变量 `record` 具有结构类型 `id`。  请注意，`pname` 被声明为指向名为 `name` 的另一个结构类型的指针。  此声明可在定义 `name` 类型之前出现。  
  
## 请参阅  
 [声明符和变量声明](../c-language/declarators-and-variable-declarations.md)