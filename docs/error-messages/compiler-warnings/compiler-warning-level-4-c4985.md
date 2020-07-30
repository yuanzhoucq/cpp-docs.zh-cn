---
title: 编译器警告（等级 4）C4985
ms.date: 11/04/2016
f1_keywords:
- C4985
helpviewer_keywords:
- C4985
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
ms.openlocfilehash: 87537e960c858cc6741108cf191fbeb2a7a2a8d7
ms.sourcegitcommit: 6e55aeb538b1c39af754f82d6f7738a18f5aa031
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87390008"
---
# <a name="compiler-warning-level-4-c4985"></a>编译器警告（等级 4）C4985

> "*symbol-name*"：以前的声明上不存在特性。

当前方法声明或定义上的 Microsoft 源代码注释语言 (SAL) 注释与早期声明上的注释不同。 方法的定义和声明中必须使用相同的 SAL 注释。

SAL 提供一组可用于描述函数如何使用参数的注释、其关于参数的假设，以及就完成所作的保证。 注释是在 sal.h 头文件中定义的。

请注意，除非项目具有指定的标志，否则 SAL 宏将不会展开 [`/analyze`](../../build/reference/analyze-code-analysis.md) 。 指定时 **`/analyze`** ，编译器可能会引发 C4985，即使没有出现警告或错误时也是如此 **`/analyze`** 。

### <a name="to-correct-this-error"></a>更正此错误

1. 在方法的定义及其所有声明上使用相同的 SAL 注释。

## <a name="see-also"></a>请参阅

[SAL 批注](../../c-runtime-library/sal-annotations.md)
