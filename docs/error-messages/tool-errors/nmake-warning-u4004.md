---
title: NMAKE 警告 U4004 |Microsoft 文档
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
ms.openlocfilehash: 532abf2f62616d6e748c9a4e34f5c983f0853276
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317175"
---
# <a name="nmake-warning-u4004"></a>NMAKE 警告 U4004
太多规则目标 targetname  
  
 已为给定的目标使用单冒号指定多个描述块 (**:**) 作为分隔符。 NMAKE 在第一个描述块中执行命令并忽略更高版本的块。  
  
 若要在多个依赖项中指定相同的目标，使用双冒号 (`::`) 为在每个依赖项的行分隔符。