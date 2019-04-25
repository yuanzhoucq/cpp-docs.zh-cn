---
title: 错误 C1853
ms.date: 11/04/2016
f1_keywords:
- C1853
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
ms.openlocfilehash: ec2d6bf6bac46cca8bdc2e3b8fe7cc6b7799d78a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165913"
---
# <a name="fatal-error-c1853"></a>错误 C1853

> '*文件名*预编译的头文件是从以前版本的编译器，或预编译标头是C++并将它从 C （或相反）

可能的原因：

- 以前的编译器版本编译预编译标头。 请尝试重新编译使用当前的编译器的标头。

- 预编译标头是C++，并且使用从 c。 请尝试重新与 C 配合使用的标头编译通过指定之一[/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)编译器选项或源文件的后缀更改为"c"。 有关详细信息，请参阅[预编译代码的两种方法](../../build/creating-precompiled-header-files.md#two-choices-for-precompiling-code)。