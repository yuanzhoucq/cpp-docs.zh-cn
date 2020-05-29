---
title: NMAKE 错误 U1100
ms.date: 11/04/2016
f1_keywords:
- U1100
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
ms.openlocfilehash: d5c62c1465bbb6463afbac2bc9ad5f4290473471
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193259"
---
# <a name="nmake-fatal-error-u1100"></a>NMAKE 错误 U1100

宏 "macroname" 在批处理规则 "rule" 的上下文中是非法的

当批处理模式规则的命令块直接或间接引用非 $ < 的特殊文件宏时，NMAKE 生成此错误。

$ < 是批处理模式规则唯一允许使用的宏。
