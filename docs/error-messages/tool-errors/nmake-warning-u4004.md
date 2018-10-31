---
title: NMAKE 警告 U4004
ms.date: 11/04/2016
f1_keywords:
- U4004
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
ms.openlocfilehash: 882f6c98b31d23d283f5e8b32b46a46c543b1a76
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436213"
---
# <a name="nmake-warning-u4004"></a>NMAKE 警告 U4004

规则目标 targetname 太多

为给定目标使用单个冒号已指定多个描述块 (**:**) 作为分隔符。 NMAKE 中的第一个描述块中执行命令，并忽略更高版本的块。

若要在多个依赖项中指定相同的目标，请使用双冒号 (`::`) 为每个依赖关系行中的分隔符。