---
title: 链接器工具错误 LNK2008 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2008
dev_langs:
- C++
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18eda06e7f133ada4de1b7ec28ac21be205a71f7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086806"
---
# <a name="linker-tools-error-lnk2008"></a>链接器工具错误 LNK2008

链接地址信息目标不是对齐 symbol_name

在没有正确对齐的对象文件中找到链接地址信息目标链接。

此错误可能由自定义 secton 对齐方式 (例如，#pragma [pack](../../preprocessor/pack.md))，[对齐](../../cpp/align-cpp.md)修饰符，或通过修改 secton 对齐方式的程序集语言代码。

如果你的代码不使用上述任一操作，这可能被引起编译器。