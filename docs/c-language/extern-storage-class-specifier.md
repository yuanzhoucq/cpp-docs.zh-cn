---
title: extern 存储类说明符
ms.date: 07/10/2018
helpviewer_keywords:
- extern keyword [C]
- storage class specifiers, extern
- extern keyword [C], storage class specifier
- external linkage, storage-class specifiers
- external linkage, extern modifier
ms.assetid: 6e16d927-291f-49e4-986c-9d91a482a441
ms.openlocfilehash: 426bf816b988730530ba52c3f995aa2b0a8f0140
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650310"
---
# <a name="extern-storage-class-specifier"></a>extern 存储类说明符

使用 extern 存储类说明符声明的变量是对变量的引用，变量名称与另一个源文件中定义的名称相同。 它用于显示外部级别变量定义。 声明为 extern 的变量没有为自己分配的存储；它只是名称。

## <a name="example"></a>示例

此示例阐释内部和外部级别的声明：

```c

// Source1.c

int i = 1;

// Source2. c

#include <stdio.h>

// Refers to the i that is defined in Source1.c:
extern int i;

void func(void);

int main()
{
    // Prints 1:
    printf_s("%d\n", i);
    func();
    return;
}

void func(void)
{
    // Address of global i assigned to pointer variable:
    static int *external_i = &i;

    // This definition of i hides the global i in Source.c:
    int i = 16;

    // Prints 16, 1:
    printf_s("%d\n%d\n", i, *external_i);
}
```

在此示例中，变量 `i` 是在 Source1.c 中定义，初始值为 1。 Source2.c 中的 extern 声明让“i”在此文件中显示。

在 `func` 函数中，全局变量 `i` 的地址用于初始化 static 指针变量 `external_i`。 此用法之所以有效是因为全局变量具有 static 生存期，这意味着其地址在程序执行期间不会更改。 接下来，变量 `i` 在 `func` 的范围内定义为初始值为 16 的局部变量。 此定义不会影响外部级别 `i` 的值（通过对局部变量使用它的名称来隐藏它）。 全局 `i` 的值现在只能通过指针 `external_i` 访问。

## <a name="see-also"></a>请参阅

[内部级别声明的存储类说明符](../c-language/storage-class-specifiers-for-internal-level-declarations.md)