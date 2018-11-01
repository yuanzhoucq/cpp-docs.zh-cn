---
title: 错误 C1853
ms.date: 11/04/2016
f1_keywords:
- C1853
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
ms.openlocfilehash: 30cf003cc81cb27f7c68b7f0a38529e2d9c88ef5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677820"
---
# <a name="fatal-error-c1853"></a>错误 C1853

> '*文件名*预编译标头文件从以前版本的编译器，或者预编译标头为 c + + 而在您使用它从 C （或相反）

可能的原因：

- 以前的编译器版本编译预编译标头。 请尝试重新编译使用当前的编译器的标头。

- 预编译标头为 c + + 和 c。 请尝试通过指定之一重新编译与 C 配合使用的标头中使用[/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)编译器选项或源文件的后缀更改为"c"。 有关详细信息，请参阅[预编译代码的两种方法](../../build/reference/creating-precompiled-header-files.md#two-choices-for-precompiling-code)。