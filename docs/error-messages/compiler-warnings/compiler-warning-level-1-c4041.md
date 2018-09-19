---
title: 编译器警告 （等级 1） C4041 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4041
dev_langs:
- C++
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ff2c8066557e420ecd7de561d7731b7be733315
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085779"
---
# <a name="compiler-warning-level-1-c4041"></a>编译器警告（等级 1）C4041

编译器限制 : 正在终止浏览器输出

浏览器信息超出了编译器限制。

使用 [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) （浏览器信息包含局部变量）进行编译可能导致该警告。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 使用 /Fr（浏览器信息不含局部变量）进行编译。

1. 禁用浏览器输出（不使用 /FR 或 /Fr 进行编译）。