---
title: 2.6.1 master 构造 |Microsoft 文档
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
ms.openlocfilehash: a60a8df380fdcc0052d8fe2d070c8d926bcb28f8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689550"
---
# <a name="261-master-construct"></a>2.6.1 master 构造
**Master**指令标识一个构造，用于指定由主线程的团队执行的结构化的块。 语法**master**指令是，如下所示：  
  
```  
#pragma omp master new-linestructured-block  
```  
  
 团队中的其他线程不会执行关联的结构化的块。 在进入或退出 master 构造上的没有隐含的屏障。