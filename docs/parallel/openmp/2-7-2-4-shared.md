---
title: 2.7.2.4 共享 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c9c5d653-58fc-4620-ab0a-443ac4f8ba2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d1a545f1c505f9f578cad682399c8d69a882824
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400141"
---
# <a name="2724-shared"></a>2.7.2.4 shared

此子句共享中出现的变量*变量列表*在团队中的所有线程之间。 发生在团队内的所有线程都访问相同的存储区域以进行**共享**变量。

语法**共享**子句如下所示：

```
shared(variable-list)
```