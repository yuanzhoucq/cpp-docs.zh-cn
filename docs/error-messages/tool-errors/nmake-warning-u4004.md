---
title: NMAKE 警告 U4004 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4004
dev_langs:
- C++
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a89bb8abf212c8a0ffa9fb40fe5d3ea43307a08
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016645"
---
# <a name="nmake-warning-u4004"></a>NMAKE 警告 U4004

规则目标 targetname 太多

为给定目标使用单个冒号已指定多个描述块 (**:**) 作为分隔符。 NMAKE 中的第一个描述块中执行命令，并忽略更高版本的块。

若要在多个依赖项中指定相同的目标，请使用双冒号 (`::`) 为每个依赖关系行中的分隔符。