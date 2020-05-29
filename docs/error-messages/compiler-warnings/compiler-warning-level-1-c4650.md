---
title: 编译器警告（等级 1）C4650
ms.date: 11/04/2016
f1_keywords:
- C4650
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
ms.openlocfilehash: e57f1d9acba4a8734339f3b8e538120abe542efc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199563"
---
# <a name="compiler-warning-level-1-c4650"></a>编译器警告（等级 1）C4650

调试信息不在预编译头中;仅标头中的全局符号可用

预编译的头文件不是用 Microsoft 符号调试信息编译的。

链接后，生成的可执行文件或动态链接库文件将不包括预编译标头中包含的本地符号的调试信息。

通过使用[/zi](../../build/reference/z7-zi-zi-debug-information-format.md)命令行选项重新编译预编译头文件，可避免此警告。
