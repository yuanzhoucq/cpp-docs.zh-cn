---
title: 错误 C1128
ms.date: 11/04/2016
f1_keywords:
- C1128
helpviewer_keywords:
- C1128
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
ms.openlocfilehash: 64671c9abe8ed1375df1e91ca7509e6a597366ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203618"
---
# <a name="fatal-error-c1128"></a>错误 C1128

超过对象文件格式限制的部分数：用/bigobj 编译

.Obj 文件超出了允许的部分数，COFF 对象文件格式限制。

达到此部分限制可能是由于使用[/gy](../../build/reference/gy-enable-function-level-linking.md)和调试生成; **/Gy**使函数进入自己的 COMDAT 部分。 在调试版本中，每个 COMDAT 函数都有一个调试信息部分。

如果内联函数太多，也可能导致 C1128。

若要更正此错误，请将您的源文件分成多个源代码文件，不带 **/gy**编译，或用[/Bigobj 编译（增加中的节数。Obj 文件）](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md)。  如果不用 **/gy**编译，则需要单独指定优化，因为 **/O2**和 **/O1**两者都隐含 **/gy**。

如果可能，请在不调试信息的情况下编译。

你可能还需要在单独的源代码文件中具有模板的特定实例化，而不是让编译器发出它们。

在移植代码时，C1128 可能会在第一次使用 x64 编译器时出现，并且在更高版本中使用 x86 编译器。 x64 至少具有4个节，与编译的每个函数相关，或者从**模板或内联**类内联：代码、pdata 和调试信息，以及可能的 xdata。  X86 不具有 pdata。
