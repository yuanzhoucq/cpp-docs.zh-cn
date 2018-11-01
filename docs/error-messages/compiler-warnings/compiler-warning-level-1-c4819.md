---
title: 编译器警告（等级 1）C4819
ms.date: 11/04/2016
f1_keywords:
- C4819
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
ms.openlocfilehash: c0ca29a304fbd05cb0c6b7d1b06414304c70fb2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596607"
---
# <a name="compiler-warning-level-1-c4819"></a>编译器警告（等级 1）C4819

该文件包含不能在当前代码页（数字）中表示的字符。 以 Unicode 格式保存该文件防止数据丢失。

在具有不能表示文件中所有字符的代码页的系统上编译 ANSI 源文件时，出现 C4819。

若要解决 C4819，请以 Unicode 格式保存该文件。 在 Visual Studio 中，选择**文件**，**高级保存选项**。 中**高级保存选项**对话框框中，选择可以表示该文件中的所有字符的编码 — 例如，UTF-8，然后选择**确定**。