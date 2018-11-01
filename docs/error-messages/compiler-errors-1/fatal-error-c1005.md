---
title: 错误 C1005
ms.date: 11/04/2016
f1_keywords:
- C1005
helpviewer_keywords:
- C1005
ms.assetid: 150daf8e-a38a-4669-9c1a-a05b5a1f65ef
ms.openlocfilehash: a84791367656729b1cbd50ca180368f6c01531a4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614456"
---
# <a name="fatal-error-c1005"></a>错误 C1005

字符串过大，无法缓冲

编译器中间文件内的字符串溢出了缓冲区。

当你传递到 [/Fd](../../build/reference/fd-program-database-file-name.md) 或 [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) 编译器选项的参数大于 256 个字节时，可能会遇到此错误。