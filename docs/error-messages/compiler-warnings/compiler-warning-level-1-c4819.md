---
title: 编译器警告 （等级 1） C4819 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4819
dev_langs:
- C++
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac468bc605c261b66f47fdf40efd1a01a5383d58
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074274"
---
# <a name="compiler-warning-level-1-c4819"></a>编译器警告（等级 1）C4819

该文件包含不能在当前代码页（数字）中表示的字符。 以 Unicode 格式保存该文件防止数据丢失。

在具有不能表示文件中所有字符的代码页的系统上编译 ANSI 源文件时，出现 C4819。

若要解决 C4819，请以 Unicode 格式保存该文件。 在 Visual Studio 中，选择**文件**，**高级保存选项**。 中**高级保存选项**对话框框中，选择可以表示该文件中的所有字符的编码 — 例如，UTF-8，然后选择**确定**。