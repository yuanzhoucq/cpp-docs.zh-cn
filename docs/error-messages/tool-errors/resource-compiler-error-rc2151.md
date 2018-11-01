---
title: 资源编译器错误 RC2151
ms.date: 11/04/2016
f1_keywords:
- RC2151
helpviewer_keywords:
- RC2151
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
ms.openlocfilehash: 8eaa50bc6080e37a4a74585eb03cbe4e40893bce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598882"
---
# <a name="resource-compiler-error-rc2151"></a>资源编译器错误 RC2151

不能重新使用字符串常量

使用相同的值在两次**STRINGTABLE**语句。 请确保您没有混合出现重复的十进制和十六进制值。

在每个 ID **STRINGTABLE**必须是唯一的。 为最大效率，请使用 16 的倍数启动连续常数。