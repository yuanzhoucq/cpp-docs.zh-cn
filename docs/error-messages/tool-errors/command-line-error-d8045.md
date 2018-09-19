---
title: 命令行错误 D8045 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8045
dev_langs:
- C++
helpviewer_keywords:
- D8045
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6838202178e8012df61d17e2434461d6f4858bf3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022781"
---
# <a name="command-line-error-d8045"></a>命令行错误 D8045

不能编译 C 文件 file 与 /clr 选项

仅 c + + 源代码文件可以传递给使用的编译 **/clr**。  使用 **/TP**以.c 文件编译为.cpp 文件; 请参阅[/Tc、 /Tp、 /TC、 /TP （指定源文件类型）](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)有关详细信息。

有关详细信息，请参阅 [/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

如果在编译时使用 Visual c + + ATL 应用程序，也可能发生 D8045。 请参阅[如何： 迁移到 /clr](../../dotnet/how-to-migrate-to-clr.md)有关详细信息。