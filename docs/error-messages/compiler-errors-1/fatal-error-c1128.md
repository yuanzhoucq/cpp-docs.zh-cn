---
title: 错误 C1128
ms.date: 11/04/2016
f1_keywords:
- C1128
helpviewer_keywords:
- C1128
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
ms.openlocfilehash: bb1d9af10084d6b3e75325450c7f13ea1683ee2e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62229041"
---
# <a name="fatal-error-c1128"></a>错误 C1128

节数超过对象文件格式限制： 使用 /bigobj 进行编译

.Obj 文件超过了允许的部分中，COFF 对象文件格式限制的数目。

达到此部分限制可能是使用的结果[/Gy](../../build/reference/gy-enable-function-level-linking.md)和调试版本;**/Gy**导致函数以转到其自己的 COMDAT 部分。 在调试版本中，没有用于每个 COMDAT 函数的调试信息节。

如果有太多的内联函数，还会导致 C1128。

若要更正此错误，将源文件拆分到多个源代码文件，而无需编译 **/Gy**，或使用编译[/bigobj （增加的节数中。Obj 文件）](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md)。  如果你不具有编译 **/Gy**，将需要单独指定优化由于 **/o2**并 **/o1**均暗指 **/Gy**。

如果可能，编译而不进行调试的信息。

您可能还需要单独的源文件的代码文件中具有特定的实例化的模板而不是让编译器发出。

移植代码时，C1128 可能时将显示第一次使用 x64 编译器，以及更高版本与 x86 编译器。 x64 将包含至少 4 个部分与编译每个函数相关联 **/Gy**或从模板或类内联内联： 代码、 pdata、 和调试信息，以及可能的 xdata。  X86 不会有 pdata。