---
title: 生存期
ms.date: 11/04/2016
helpviewer_keywords:
- local variables, lifetime
- variables, automatic
- storage classes, lifetime
- variables, lifetime
- automatic storage class
- automatic storage class, duration
- storage class specifiers, storage duration
- memory allocation, dynamic allocation
- functions [C++], lifetime
- storage duration
- dynamic memory allocation
- memory allocation, dynamic
- lifetime
- global variables, lifetime
ms.assetid: ff0b42cb-3f0f-49a3-a94f-d1d825d8ddfe
ms.openlocfilehash: 752230db54727516e0c48c0621eaadc59486e2e4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218840"
---
# <a name="lifetime"></a>生存期

“生存期”是其中存在变量或函数的程序执行的时段。 标识符的存储持续时间决定其生存期。

使用 storage-class-specifier `static` 声明的标识符有静态存储持续时间。 具有静态存储持续时间的标识符（也称为“全局”）具有存储和程序持续时间的定义值。 将保留存储，并且在程序启动前只将标识符的存储值初始化一次。 使用外部或内部链接声明的标识符还具有静态存储持续时间（请参阅[链接](../c-language/linkage.md)）。

在函数内部没有使用 `static` 存储类说明符声明的标识符有自动存储持续时间。 具有自动存储持续时间的标识符（“本地标识符”）具有存储和已定义的值（仅在定义或声明该标识符的块中）。 程序每次进入该块时都将为自动标识符分配新存储，并在程序退出该块时丢失其存储（及其值）。 函数中声明的不具有链接的标识符也具有自动存储持续时间。

以下规则指定标识符是具有全局（静态）还是局部（自动）生存期：

- 所有函数都具有静态生存期。 因此，它们在程序执行期间始终存在。 在外部级别（即，在同一级别函数定义的程序中的所有块之外）声明的标识符始终具有全局（静态）生存期。

- 如果局部变量有初始值设定项，则此变量在每次创建时都会进行初始化（除非它被声明为 `static`）。 函数参数也具有本地生存期。 通过在标识符声明中添加 `static` 存储类说明符，可以为块中的标识符指定全局生存期。 一旦声明了 `static`，变量就会将它的值从块中的一个条目保留到下一个条目。

尽管有全局生存期的标识符（例如，外部声明的变量或使用 `static` 关键字声明的局部变量）在源程序的整个执行过程中都存在，但它可能并不在程序的所有部分中都可见。 有关可见性的信息，请参阅[范围和可见性](../c-language/scope-and-visibility.md)；有关 storage-class-specifier  非终止符的讨论，请参阅[存储类](../c-language/c-storage-classes.md)。

如果通过使用特殊库例程（如 `malloc`）创建，则可以根据需要分配内存（动态）。 由于动态内存分配使用库例程，因此它不被视为语言的一部分。 请参阅《运行时库参考》  中的 [malloc](../c-runtime-library/reference/malloc.md) 函数。

## <a name="see-also"></a>请参阅

[生存期、范围、可见性和链接](../c-language/lifetime-scope-visibility-and-linkage.md)
