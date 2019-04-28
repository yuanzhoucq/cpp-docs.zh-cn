---
title: NMAKE 错误 U1100
ms.date: 11/04/2016
f1_keywords:
- U1100
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
ms.openlocfilehash: a1474acab4ca4929fb4db4b7b78d7a96637a0745
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298277"
---
# <a name="nmake-fatal-error-u1100"></a>NMAKE 错误 U1100

宏 macroname 是在批处理规则 rule 的上下文中非法

当批模式规则的命令块直接或间接引用不是 $ 的特殊文件宏时，NMAKE 生成该错误 <。

$< 唯一允许的批模式规则的宏。