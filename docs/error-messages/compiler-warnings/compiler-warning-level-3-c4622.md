---
title: 编译器警告（等级 3）C4622
ms.date: 11/04/2016
f1_keywords:
- C4622
helpviewer_keywords:
- C4622
ms.assetid: d3c879f0-4492-4f4b-b26d-230993f3a933
ms.openlocfilehash: 295a183afb24121a2abefd336f6ea92110220155
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185499"
---
# <a name="compiler-warning-level-3-c4622"></a>编译器警告（等级 3）C4622

覆盖创建对象文件的预编译头期间生成的调试信息：“file”

当使用 [/Yu](../../build/reference/yu-use-precompiled-header-file.md) （使用预编译头）选项编译时，指定文件中的 CodeView 信息丢失。

当创建或使用预编译头文件时（使用 [/Fo](../../build/reference/fo-object-file-name.md)）重命名对象文件，并使用新对象文件进行链接。
