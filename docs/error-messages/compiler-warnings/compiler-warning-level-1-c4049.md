---
title: 编译器警告 （等级 1） C4049 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4049
dev_langs:
- C++
helpviewer_keywords:
- C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 68a89d02129e5e8fbedb0649fff0cfe3813304c5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053513"
---
# <a name="compiler-warning-level-1-c4049"></a>编译器警告 （等级 1） C4049

编译器限制： 显示终止行号

该文件包含多个 16777215 (2<sup>24</sup>-1) 源行。 编译器停止在 16,777,215 编号。

对于行 16,777,215 后的代码：

- 映像将包含没有调试信息的行号。

- 一些诊断可能会报告与错误的行号。

- .asm 列表 (/ FAs) 可能具有不正确的行号。