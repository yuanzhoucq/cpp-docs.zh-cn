---
title: 指针声明
ms.date: 11/04/2016
helpviewer_keywords:
- pointer declarations
- declarations, pointers
- const keyword [C]
- pointers, declarations
ms.assetid: 8b3b7fc7-f44d-480d-b6f9-cebe4e5462a6
ms.openlocfilehash: 31d7e30859537fed1b18f6d30302d83248e17e74
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211757"
---
# <a name="pointer-declarations"></a>指针声明

“指针声明”可命名指针变量并指定该变量所指向的对象的类型。 声明为指针的变量保留了一个内存地址。

## <a name="syntax"></a>语法

*declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(** *declarator* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **[** *constant-expression*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **(** *parameter-type-list* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **(** *identifier-list*<sub>opt</sub> **)**

*pointer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *type-qualifier-list*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *type-qualifier-list*<sub>opt</sub> *pointer*

*type-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier-list* *type-qualifier*

*type-specifier* 用于指定对象的类型，可以是任何基本、结构或联合类型。 指针变量也可以指向函数、数组和其他指针。 （有关声明和解释更复杂的指针类型的信息，请参阅[解释更复杂的声明符](../c-language/interpreting-more-complex-declarators.md)。）

通过将 type-specifier 设为 `void`，可以延迟指定指针所引用的类型。 这样的项被称为“指向 `void` 的指针”，并被写成 `void *`。 声明为指向 *void* 的指针的变量可用于指向任何类型的对象。 但是，若要对指针或指针指向的对象执行大多数操作，则必须为每个操作显式指定指针指向的类型。 （类型为 `char` \* 和 `void` \* 的变量是赋值兼容的，不需要强制转换类型。此类转换可使用类型强制转换完成（有关详细信息，请参阅[类型强制转换](../c-language/type-cast-conversions.md)）。

type-qualifier 可以是 `const` 和/或 `volatile`。 它们分别指定了指针不能被程序本身修改 (`const`)，或指针可以被超出程序的控制范围的某进程以合法方式修改 (`volatile`)。 （若要详细了解 `const` 和 `volatile`，请参阅[类型限定符](../c-language/type-qualifiers.md)。）

*declarator* 可为变量命名，并可包含类型修饰符。 例如，如果 *declarator* 表示数组，则将指针的类型修改为指向数组的指针。

在定义结构、联合或枚举类型之前，您可以声明指向结构、联合或枚举类型的指针。 您可使用结构或联合标记声明指针，如下面的示例所示。 此类声明是允许的，因为编译器不需要知道要为指针变量分配空间的结构或联合的大小。

## <a name="examples"></a>示例

以下示例演示了指针声明。

```
char *message; /* Declares a pointer variable named message */
```

message 指针指向 `char` 类型的变量。

```
int *pointers[10];  /* Declares an array of pointers */
```

pointer 数组有 10 个元素；每个元素都是指向 `int` 类型的变量的指针。

```
int (*pointer)[10]; /* Declares a pointer to an array of 10 elements */
```

指针  变量指向具有 10 个元素的数组。 此数组中的每个元素都是 `int` 类型。

```
int const *x;      /* Declares a pointer variable, x,
                      to a constant value */
```

可以将指针 x 修改为指向不同的 `int` 值，但无法修改它所指向的值。

```
const int some_object = 5 ;
int other_object = 37;
int *const y = &fixed_object;
int volatile *const z = &some_object;
int *const volatile w = &some_object;
```

这些声明中的变量 y 被声明为指向 `int` 值的常数指针。 可以修改该指针指向的值，但指针本身必须始终指向同一位置：*fixed_object* 的地址。 同样，z 也是常数指针，而它也被声明为指向值不能被程序修改的 `int`。 附加说明符 `volatile` 指明，尽管 z 所指向的 const int 的值不能被程序修改，但可以被当前与程序并发运行的进程以合法方式修改。 *w* 的声明指定，程序无法更改指向的值，并且程序无法修改指针。

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

变量 *line* 具有名为 *list* 的结构类型。 list 结构类型有三个成员：第一个成员是指向 `char` 值的指针，第二个成员是 `int` 值，第三个成员是指向另一个 list 结构的指针。

```
struct id
{
    unsigned int id_no;
    struct name *pname;
} record;
```

变量 *record* 具有结构类型 *id*。请注意，*pname* 被声明为指向名为 *name* 的另一个结构类型的指针。 此声明可在定义 *name* 类型之前出现。

## <a name="see-also"></a>请参阅

[声明符和变量声明](../c-language/declarators-and-variable-declarations.md)
