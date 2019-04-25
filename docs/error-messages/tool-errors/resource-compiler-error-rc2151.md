---
title: 资源编译器错误 RC2151
ms.date: 11/04/2016
f1_keywords:
- RC2151
helpviewer_keywords:
- RC2151
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
ms.openlocfilehash: 8eaa50bc6080e37a4a74585eb03cbe4e40893bce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173439"
---
# <a name="resource-compiler-error-rc2151"></a>资源编译器错误 RC2151

不能重新使用字符串常量

使用相同的值在两次**STRINGTABLE**语句。 请确保您没有混合出现重复的十进制和十六进制值。

在每个 ID **STRINGTABLE**必须是唯一的。 为最大效率，请使用 16 的倍数启动连续常数。