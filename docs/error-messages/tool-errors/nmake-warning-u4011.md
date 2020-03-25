---
title: NMAKE 警告 U4011
ms.date: 11/04/2016
f1_keywords:
- U4011
helpviewer_keywords:
- U4011
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
ms.openlocfilehash: 6b1701ffc83f849d2482bd14b25d65c04c496899
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193142"
---
# <a name="nmake-warning-u4011"></a>NMAKE 警告 U4011

"target"：并非所有依赖项都可用;未生成目标

给定目标的依赖项不存在或已过期，并且用于更新依赖项的命令返回非零退出代码。 /K 选项告诉 NMAKE 继续处理生成的无关部分，并在 NMAKE 会话结束时发出退出代码1。

对于无法创建或更新的每个依赖项，此警告前面会出现警告[U4010](../../error-messages/tool-errors/nmake-warning-u4010.md) 。
