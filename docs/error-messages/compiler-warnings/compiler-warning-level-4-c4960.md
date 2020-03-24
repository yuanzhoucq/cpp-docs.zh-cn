---
title: 编译器警告（等级 4）C4960
ms.date: 11/04/2016
f1_keywords:
- C4960
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
ms.openlocfilehash: 286d3a1953c6c6badf15b712feac99afafe8b0a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198115"
---
# <a name="compiler-warning-level-4-c4960"></a>编译器警告（等级 4）C4960

“function”太大，无法配置

当使用 [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)时，编译器检测到某个输入模块的函数具有的指令超过 65,535 条。 如此大的函数不可用于按配置进行的优化。

若要解决此警告，请减小该函数的大小。
