---
title: 2.7.2.8 copyprivate |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c382348c-c785-45b2-8ee6-a66b76b97f3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6815afe12344f94ed33d6b9260472f3e29eb72a0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46406355"
---
# <a name="2728-copyprivate"></a>2.7.2.8 copyprivate

**Copyprivate**子句提供了一种机制来使用私有变量广播来自团队的成员的其他成员的值。 它是使用共享的变量值时提供此类共享的变量会很困难 （例如，在需要在每个级别的不同变量的递归） 的替代方法。 **Copyprivate**子句仅可出现在**单个**指令。

语法**copyprivate**子句如下所示：

```

copyprivate(
variable-list
)

```

效果**copyprivate**其变量列表中的变量上的子句与关联的结构化块执行后会发生**单个**构造，并在任何中的线程前团队已离开构造结束时的障碍。 然后，在团队中每个变量中的所有其他线程*变量列表*，该变量将成为使用相应的值定义 （像是通过赋值） 中执行构造的线程的变量的结构化块。

限制**copyprivate**子句如下所示：

- 中指定的变量**copyprivate**子句不能出现在**专用**或**firstprivate**子句相同**单**指令。

- 如果**单个**指令与**copyprivate**并行区域的动态范围中遇到子句中指定的所有变量**copyprivate**子句必须是在封闭上下文中的私钥。

- 中指定的变量**copyprivate**子句必须具有可访问的明确复制赋值运算符。