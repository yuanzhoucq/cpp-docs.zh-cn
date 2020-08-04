---
title: 复合语句 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- compound statements
- statements, compound
ms.assetid: 32d1bf86-cbbc-42a9-ba3a-1be1c6c7754c
ms.openlocfilehash: 93f7fd24049c744874fb0ab3bda37eedef3a139a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87200577"
---
# <a name="compound-statement-c"></a>复合语句 (C)

复合语句（亦称为“块”）通常作为另一条语句（如 `if` 语句）的主体出现。 [声明和类型](../c-language/declarations-and-types.md)描述可在复合语句的头部出现的声明的格式和含义。

## <a name="syntax"></a>语法

compound-statement  ：<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *declaration-list*<sub>opt</sub> *statement-list*<sub>opt</sub> **}**

declaration-list  ：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-list* *declaration*

statement-list  ：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement-list* *statement*

如果有声明，则它们必须在任何语句之前出现。 在复合语句开头声明的每个标识符的范围从其声明点扩展到块的末尾。 它在整个块中都可见，除非内部块中存在对同一标识符的声明。

复合语句中的标识符被假定为 `auto`，除非另外使用 `register`、`static` 或 `extern`（只能是 `extern` 的函数除外）显式声明。 可以在函数声明中去掉 `extern` 说明符，但函数仍然是 `extern`。

如果在包含存储类 `extern` 的复合语句中声明变量或函数，则不会分配存储，也不允许初始化。 声明引用在其他位置定义的外部变量或函数。

使用 `auto` 或 `register` 关键字在块中声明的变量在每次进入复合语句时重新分配并初始化（如果需要）。 在退出复合语句后将不再定义这些变量。 如果在块内声明的变量有 `static` 特性，则此变量在程序开始执行时初始化，并在整个程序中保持值不变。 若要了解 `static`，请参阅[存储类](../c-language/c-storage-classes.md)。

此示例演示了一个复合语句：

```
if ( i > 0 )
{
    line[i] = x;
    x++;
    i--;
}
```

在此示例中，如果 `i` 大于 0，则复合语句内的所有语句将按顺序执行。

## <a name="see-also"></a>请参阅

[语句](../c-language/statements-c.md)
