---
title: NMAKE 错误 U1059 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1059
dev_langs:
- C++
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b54919398c757bfe05f747ff57341f31decfc61
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200785"
---
# <a name="nmake-fatal-error-u1059"></a>NMAKE 错误 U1059

> 语法错误:} 从属项中缺少

未正确指定一个相关的搜索路径。 存在的路径或右大括号中的空格 (**}**) 被省略。

一个相关的目录规范的语法是

> **{** *目录* **} 依赖**

其中*目录*指定一个或多个路径，每个由分号分隔 (**;**)。 不允许有空格。

如果搜索路径的一部分或全部由宏替换，请确保将在宏扩展中不存在空格。