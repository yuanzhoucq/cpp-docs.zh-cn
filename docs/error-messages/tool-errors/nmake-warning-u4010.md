---
title: NMAKE 警告 U4010
ms.date: 11/04/2016
f1_keywords:
- U4010
helpviewer_keywords:
- U4010
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
ms.openlocfilehash: f68da1893eec6325ccccfd0e2e2dd0e612f28eb9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193129"
---
# <a name="nmake-warning-u4010"></a>NMAKE 警告 U4010

"target"：生成失败;已指定/k，正在继续 。

给定目标的命令块中的命令返回非零退出代码。 /K 选项告诉 NMAKE 继续处理生成的无关部分，并在 NMAKE 会话结束时发出退出代码1。

如果给定的目标是本身，它是另一个目标的依赖项，则 NMAKE 在此警告之后发出警告[U4011](../../error-messages/tool-errors/nmake-warning-u4011.md) 。
