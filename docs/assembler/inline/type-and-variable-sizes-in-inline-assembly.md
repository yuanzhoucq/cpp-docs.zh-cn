---
title: 内联程序集中的类型和变量大小
ms.date: 08/30/2018
ms.topic: reference
helpviewer_keywords:
- variables, length
- size, getting in inline assembly
- size
- LENGTH operator
- TYPE operator
- SIZE operator
- inline assembly, operators
- variables, type
- variables, size
ms.assetid: b62c2f2b-a7ad-4145-bae4-d890db86d348
ms.openlocfilehash: bc98c8561a7fd06f875781802558cdd7e71a67ec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169235"
---
# <a name="type-and-variable-sizes-in-inline-assembly"></a>内联程序集中的类型和变量大小

**Microsoft 专用**

在内联程序集中，**长度**、**大小**和**类型**运算符具有有限含义。 无法将这些运算符与 `DUP` 运算符一起使用（因为您无法利用 MASM 指令或运算符定义数据）。 但是，您可以使用它们来查找 C 或 C++ 变量或类型的大小：

- **LENGTH**运算符可以返回数组中的元素数。 它为非数组变量返回值 1。

- **大小**运算符可返回 C 或C++变量的大小。 变量的大小是其**长度**和**类型**的乘积。

- **类型**运算符可以返回 C 或C++类型或变量的大小。 如果变量是数组，则**TYPE**返回数组的单个元素的大小。

例如，如果程序具有8元素**int**数组，

```cpp
int arr[8];
```

则下列 C 和程序集表达式将生成 `arr` 及其元素的大小。

|__asm|C|大小|
|-------------|-------|----------|
|**长度**arr|`sizeof`(arr)/`sizeof`(arr[0])|8|
|**大小**arr|`sizeof`(arr)|32|
|**键入**arr|`sizeof`(arr[0])|4|

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
