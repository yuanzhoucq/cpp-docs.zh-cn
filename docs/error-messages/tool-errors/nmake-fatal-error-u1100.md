---
title: NMAKE 错误 U1100 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1100
dev_langs:
- C++
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27ffd33a0a80056ee57f5f088823d7f8f6549c24
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46135747"
---
# <a name="nmake-fatal-error-u1100"></a>NMAKE 错误 U1100

宏 macroname 是在批处理规则 rule 的上下文中非法

当批模式规则的命令块直接或间接地引用非 $< 的特殊文件宏时，NMAKE 生成该错误。

$< 是批模式规则唯一可以使用的宏。