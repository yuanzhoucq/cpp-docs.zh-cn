---
title: NMAKE 错误 U1059
ms.date: 08/27/2018
f1_keywords:
- U1059
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
ms.openlocfilehash: 33be3312e1f0aaa7f1e8aad64b44ea9aefd25346
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182833"
---
# <a name="nmake-fatal-error-u1059"></a>NMAKE 错误 U1059

> 语法错误：依赖项中缺少 "}"

未正确指定依赖项的搜索路径。 路径中存在空格，或者省略了右大括号（ **}** ）。

依赖项的目录规范的语法是

> **{** *directory* **} 依赖项**

其中，*目录*指定了一个或多个路径，每个路径由分号（ **;** ）分隔。 不允许使用空格。

如果 "部分" 或 "全部" 搜索路径被宏替代，请确保宏扩展中不存在空格。
