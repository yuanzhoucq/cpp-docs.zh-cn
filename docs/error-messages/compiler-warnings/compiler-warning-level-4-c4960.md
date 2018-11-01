---
title: 编译器警告（等级 4）C4960
ms.date: 11/04/2016
f1_keywords:
- C4960
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
ms.openlocfilehash: ff4a9b3d78a108a45abb18c22049b104e630bf15
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516358"
---
# <a name="compiler-warning-level-4-c4960"></a>编译器警告（等级 4）C4960

“function”太大，无法配置

当使用 [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)时，编译器检测到某个输入模块的函数具有的指令超过 65,535 条。 如此大的函数不可用于按配置进行的优化。

若要解决此警告，请减小该函数的大小。