---
title: NMAKE 错误 U1100
description: Microsoft NMAKE 严重错误 U1100 的原因说明。
ms.date: 07/17/2020
f1_keywords:
- U1100
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
ms.openlocfilehash: f908514469a6c9fdb53df3b2bded1b30bddc5a41
ms.sourcegitcommit: 00af3df3331854b23693ee844e5e7c10c8b05a90
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2020
ms.locfileid: "86491383"
---
# <a name="nmake-fatal-error-u1100"></a>NMAKE 错误 U1100

> 宏 "*宏名*" 在批处理规则 "*rule-name*" 的上下文中是非法的

当批处理模式规则的命令块直接或间接引用了不是的特殊文件宏时，NMAKE 生成此错误 `$<` 。

`$<`是批处理模式规则唯一允许的宏。

有关批处理规则中 NMAKE 宏的详细信息，请参阅[特殊 NMAKE 宏](../../build/reference/special-nmake-macros.md)。
