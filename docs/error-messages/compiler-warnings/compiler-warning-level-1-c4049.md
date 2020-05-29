---
title: 编译器警告（等级1） C4049
ms.date: 11/04/2016
f1_keywords:
- C4049
helpviewer_keywords:
- C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
ms.openlocfilehash: 214ccae5d9835bc4a3b66bbbe1cd5ded4bc651cb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164139"
---
# <a name="compiler-warning-level-1-c4049"></a>编译器警告（等级1） C4049

编译器限制：发射的终止行号

文件包含的源行超过16777215（2<sup>24</sup>-1）。 编译器停止编号为16777215。

对于第16777215行后面的代码：

- 该映像不包含行号的调试信息。

- 某些诊断可能报告了错误的行号。

- .asm 列表（/FAs）的行号可能不正确。
