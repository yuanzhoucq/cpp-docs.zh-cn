---
title: 2.6.1 master 构造 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c092064b-ea57-4d4e-9c99-a004d65656fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d82ae673e428c635172f35f9b0f682aa65dc2b8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445628"
---
# <a name="261-master-construct"></a>2.6.1 master 构造

**主**指令标识一个构造，它指定由团队的主线程执行的结构化的块。 语法**主**指令是按如下所示：

```
#pragma omp master new-linestructured-block
```

团队中的其他线程才会执行相关联的结构化的块。 没有任何隐式的屏障进入或退出 master 构造上。