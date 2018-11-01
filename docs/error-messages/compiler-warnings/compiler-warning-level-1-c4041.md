---
title: 编译器警告（等级 1）C4041
ms.date: 11/04/2016
f1_keywords:
- C4041
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
ms.openlocfilehash: 6e1f2a2396447038f6a117f66d4002bea7fd7486
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513667"
---
# <a name="compiler-warning-level-1-c4041"></a>编译器警告（等级 1）C4041

编译器限制 : 正在终止浏览器输出

浏览器信息超出了编译器限制。

使用 [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) （浏览器信息包含局部变量）进行编译可能导致该警告。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 使用 /Fr（浏览器信息不含局部变量）进行编译。

1. 禁用浏览器输出（不使用 /FR 或 /Fr 进行编译）。