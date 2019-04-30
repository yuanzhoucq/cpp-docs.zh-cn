---
title: NMAKE 错误 U1059
ms.date: 08/27/2018
f1_keywords:
- U1059
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
ms.openlocfilehash: 3c148bf2feb7ba12686e00b29f5bf90cb9f2f2d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367286"
---
# <a name="nmake-fatal-error-u1059"></a>NMAKE 错误 U1059

> 语法错误:} 从属项中缺少

未正确指定一个相关的搜索路径。 存在的路径或右大括号中的空格 (**}**) 被省略。

一个相关的目录规范的语法是

> **{** *directories* **}dependent**

其中*目录*指定一个或多个路径，每个由分号分隔 (**;**)。 不允许有空格。

如果搜索路径的一部分或全部由宏替换，请确保将在宏扩展中不存在空格。