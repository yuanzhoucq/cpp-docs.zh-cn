---
title: 编译器警告（等级 1）C4650
ms.date: 11/04/2016
f1_keywords:
- C4650
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
ms.openlocfilehash: ea3f1b6e792239692960e74c8360c6c3a1323815
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393527"
---
# <a name="compiler-warning-level-1-c4650"></a>编译器警告（等级 1）C4650

调试信息不在预编译标头;将可仅从标头的全局符号

未使用 Microsoft 符号化调试信息编译预编译的头文件。

链接时，生成的可执行文件或动态链接库文件将包含调试信息包含在预编译标头中的本地符号。

通过重新编译使用预编译的头文件可以避免此警告[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)命令行选项。