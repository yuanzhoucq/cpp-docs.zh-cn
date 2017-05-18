---
title: "指针声明 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- pointer declarations
- declarations, pointers
- const keyword [C]
- pointers, declarations
ms.assetid: 8b3b7fc7-f44d-480d-b6f9-cebe4e5462a6
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 02f33a5cd41dbbf45047915e3ad890311eba8cca
ms.contentlocale: zh-cn
ms.lasthandoff: 04/04/2017

---
# <a name="pointer-declarations"></a>指针声明
“指针声明”可命名指针变量并指定该变量所指向的对象的类型。 声明为指针的变量保留了一个内存地址。  
  
## <a name="syntax"></a>语法  
 *declarator*:  
 &nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*  
  
 *direct-declarator*：  
 &nbsp;&nbsp;*identifier*  
  
 &nbsp;&nbsp;**(** *declarator* **)**  
  
 &nbsp;&nbsp;*direct-declarator* **[** *constant-expression*<sub>opt</sub> **]**  
  
 &nbsp;&nbsp;*direct-declarator* **(** *parameter-type-list* **)**  
  
 &nbsp;&nbsp;*direct-declarator* **(** *identifier-list*<sub>opt</sub> **)**  
  
 *pointer*:  
 &nbsp;&nbsp;**\*** *type-qualifier-list*<sub>opt</sub>  
  
 &nbsp;&nbsp;**\*** *type-qualifier-list*<sub>opt</sub> *pointer*  
  
 *type-qualifier-list*:  
 &nbsp;&nbsp;*type-qualifier*  
  
 &nbsp;&nbsp;*type-qualifier-list* *type-qualifier*  
  
 *type-specifier* 用于指定对象的类型，可以是任何基本、结构或联合类型。 指针变量也可以指向函数、数组和其他指针。 （有关声明和解释更复杂的指针类型的信息，请参阅[解释更复杂的声明符](../c-language/interpreting-more-complex-declarators.md)。）  
  
 通过将 *type-specifier* 设为 **void**，可以延迟指针引用的类型的规范。 这种项称为“指向 **void** 的指针”，作为 `void *` 写入。 声明为指向 *void* 的指针的变量可用于指向任何类型的对象。 但是，若要对指针或指针指向的对象执行大多数操作，则必须为每个操作显式指定指针指向的类型。 （**char \*** 类型和 **void \*** 类型的变量不用类型强制转换即可赋值兼容。）此类转换可使用类型强制转换完成（有关详细信息，请参阅[类型强制转换](../c-language/type-cast-conversions.md)）。  
  
 *type-qualifier* 可以是 **const** 或 **volatile** 之一，也可以是这两者。 它们分别指定了程序本身无法修改的指针 (**const**)，或程序的控制之外的某些进程可以合理修改的指针 (**volatile**)。 （有关 **const** 和 **volatile** 的详细信息，请参阅[类型限定符](../c-language/type-qualifiers.md)。）  
  
 *declarator* 可为变量命名，并可包含类型修饰符。 例如，如果 *declarator* 表示数组，则将指针的类型修改为指向数组的指针。  
  
 在定义结构、联合或枚举类型之前，您可以声明指向结构、联合或枚举类型的指针。 您可使用结构或联合标记声明指针，如下面的示例所示。 此类声明是允许的，因为编译器不需要知道要为指针变量分配空间的结构或联合的大小。  
  
## <a name="examples"></a>示例  
 以下示例演示了指针声明。  
  
```  
char *message; /* Declares a pointer variable named message */  
```  
  
 message 指针指向具有 **char** 类型的变量。  
  
```  
int *pointers[10];  /* Declares an array of pointers */  
```  
  
 指针数组有 10 个元素；每个元素都是一个指向具有 **int** 类型的变量的指针。  
  
```  
int (*pointer)[10]; /* Declares a pointer to an array of 10 elements */  
```  
  
 指针变量指向具有 10 个元素的数组。 此数组中的每个元素都有 **int** 类型。  
  
```  
int const *x;      /* Declares a pointer variable, x,  
                      to a constant value */   
```  
  
 可以将指针 *x* 修改为指向不同的 **int** 值，但无法修改该指针指向的值。  
  
```  
const int some_object = 5 ;  
int other_object = 37;  
int *const y = &fixed_object;  
int volatile *const z = &some_object;  
int *const volatile w = &some_object;  
```  
  
 这些声明中的变量 *y* 被声明为指向 **int** 值的常量指针。 可以修改该指针指向的值，但指针本身必须始终指向同一位置：*fixed_object* 的地址。 同样，*z* 是常量指针，但它也被声明为指向值不能由程序修改的 **int**。 附加说明符 **volatile** 指示，尽管程序无法修改 *z* 所指向的 **const int** 的值，但当前与程序一起运行的进程可以合理地修改该值。 *w* 的声明指定，程序无法更改指向的值，并且程序无法修改指针。  
  
```  
struct list *next, *previous; /* Uses the tag for list */  
```  
  
 本示例声明了指向结构类型 *list* 的两个指针变量 *next* 和 *previous*。 只要 *list* 类型定义与声明具有相同的可见性，此声明就可以出现在 *list* 结构类型的定义前面（请参阅下一个示例）。  
  
```  
struct list   
{  
    char *token;  
    int count;  
    struct list *next;  
} line;  
```  
  
 变量 *line* 具有名为 *list* 的结构类型。 *list* 结构类型有三个成员：第一个成员是指向 **char** 值的指针，第二个成员是 **int** 值，第三个成员是指向另一个 *list* 结构的指针。  
  
```  
struct id   
{  
    unsigned int id_no;  
    struct name *pname;  
} record;  
```  
  
 变量 *record* 具有结构类型 *id*。 请注意，*pname* 被声明为指向名为 *name* 的另一个结构类型的指针。 此声明可在定义 *name* 类型之前出现。  
  
## <a name="see-also"></a>另请参阅  
 [声明符和变量声明](../c-language/declarators-and-variable-declarations.md)
