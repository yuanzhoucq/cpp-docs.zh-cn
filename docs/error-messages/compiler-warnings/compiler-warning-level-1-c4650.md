---
title: 编译器警告 （等级 1） C4650 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4650
dev_langs:
- C++
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d49b21452465f26d6e696f928c04c20dc0e33307
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052878"
---
# <a name="compiler-warning-level-1-c4650"></a>编译器警告（等级 1）C4650

调试信息不在预编译标头;将可仅从标头的全局符号

未使用 Microsoft 符号化调试信息编译预编译的头文件。

链接时，生成的可执行文件或动态链接库文件将包含调试信息包含在预编译标头中的本地符号。

通过重新编译使用预编译的头文件可以避免此警告[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)命令行选项。