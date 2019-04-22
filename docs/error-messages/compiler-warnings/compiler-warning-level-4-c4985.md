---
title: 编译器警告（等级 4）C4985
ms.date: 11/04/2016
helpviewer_keywords:
- C4985
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
ms.openlocfilehash: 73abb166910cc421f042d22d67efc122e416bceb
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024434"
---
# <a name="compiler-warning-level-4-c4985"></a>编译器警告（等级 4）C4985

“symbol name”: 先前声明中不存在特性。

当前方法声明或定义上的 Microsoft 源代码注释语言 (SAL) 注释与早期声明上的注释不同。 方法的定义和声明中必须使用相同的 SAL 注释。

SAL 提供一组可用于描述函数如何使用参数的注释、其关于参数的假设，以及就完成所作的保证。 注释是在 sal.h 头文件中定义的。

请注意，除非项目具有指定的 [/analyze](../../build/reference/analyze-code-analysis.md) 标志，否则 SAL 宏将不会展开。 在指定 **/analyze**时，即使警告和错误均显示有 **/analyze**，编译器也会引发 C4985。

### <a name="to-correct-this-error"></a>更正此错误

1. 在方法的定义及其所有声明上使用相同的 SAL 注释。

## <a name="see-also"></a>请参阅

[SAL 批注](../../c-runtime-library/sal-annotations.md)