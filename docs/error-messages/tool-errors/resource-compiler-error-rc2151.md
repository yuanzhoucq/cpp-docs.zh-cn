---
title: 资源编译器错误 RC2151 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2151
dev_langs:
- C++
helpviewer_keywords:
- RC2151
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a15f3f1237df9e4b706a2c2048dddd6d5db395d5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109777"
---
# <a name="resource-compiler-error-rc2151"></a>资源编译器错误 RC2151

不能重新使用字符串常量

使用相同的值在两次**STRINGTABLE**语句。 请确保您没有混合出现重复的十进制和十六进制值。

在每个 ID **STRINGTABLE**必须是唯一的。 为最大效率，请使用 16 的倍数启动连续常数。