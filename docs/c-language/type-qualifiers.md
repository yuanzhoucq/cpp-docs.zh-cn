---
title: 类型限定符
ms.date: 11/04/2016
helpviewer_keywords:
- volatile keyword [C], type qualifier
- type qualifiers
- volatile keyword [C]
- qualifiers for types
- const keyword [C]
- memory, access using volatile
- volatile keyword [C], type specifier
ms.assetid: bb4c6744-1dd7-40a8-b4eb-f5585be30908
ms.openlocfilehash: 729e9f65fd1054b8381f45b81e5276846145ebc1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87198718"
---
# <a name="type-qualifiers"></a>类型限定符

类型限定符为标识符提供两个属性之一。 `const` 类型限定符将对象声明为不可修改。 `volatile` 类型限定符声明了一个项，此项的值可以被超出此项所在程序的控制范围的某个项（如并发执行的线程）以合法方式更改。

`const` 和 `volatile` 这两个类型限定符只能在声明中出现一次。 类型限定符可与任何类型说明符一起出现；但是，它们不能在多项声明中的第一个逗号的后面出现。 例如，以下声明是合法的：

```
typedef volatile int VI;
const int ci;
```

以下声明是非法的：

```
typedef int *i, volatile *vi;
float f, const cf;
```

仅当访问作为表达式的左值的标识符时，类型限定符才会相关。 有关左值和表达式的信息，请参阅[左值表达式和右值表达式](../c-language/l-value-and-r-value-expressions.md)。

## <a name="syntax"></a>语法

*type-qualifier*: **constvolatile**

以下是合法的 `const` 和 `volatile` 声明：

```
int const *p_ci;       /* Pointer to constant int */
int const (*p_ci);     /* Pointer to constant int */
int *const cp_i;       /* Constant pointer to int */
int (*const cp_i);     /* Constant pointer to int */
int volatile vint;     /* Volatile integer        */
```

如果数组类型的规范包括类型限定符，则将限定元素而不是数组类型。 如果函数类型的规范包括限定符，则行为是不确定的。 `volatile` 和 `const` 都不会影响值的范围或对象的算术属性。

以下列表描述了如何使用 `const` 和 `volatile`。

- `const` 关键字可用于修改任何基本或聚合类型，或修改指向任何类型的对象的指针或 `typedef`。 如果某项声明为只包含 `const` 类型限定符，则其类型被视为 const int。`const` 变量可以被初始化，也可以被置于存储的只读区域中。 `const` 关键字对于声明指向 `const` 的指针很有用，因为这要求函数不以任何方式更改指针。

- 编译器假定，在程序运行的任何时刻，使用或修改 `volatile` 变量的值的未知进程都可以访问此变量。 因此，无论在命令行上指定了哪些优化，都必须为对 `volatile` 变量的每次赋值或引用生成代码，即使它看起来没有任何效果。

   如果单独使用 `volatile`，则假定为 `int`。 `volatile` 类型说明符可用于提供对特殊内存位置的可靠访问。 将 `volatile` 用于数据对象，这些对象可能会被信号处理程序、并行执行的程序或特殊硬件（如内存映射的 I/O 控制寄存器）访问或更改。 可以将变量在其生存期内声明为 `volatile`，也可以将单个引用强制转换为 `volatile`。

- 一个项可以同时是 `const` 和 `volatile`，在这种情况下，此项不能被它自己的程序以合法方式修改，但能被一些异步进程修改。

## <a name="see-also"></a>请参阅

[声明和类型](../c-language/declarations-and-types.md)
