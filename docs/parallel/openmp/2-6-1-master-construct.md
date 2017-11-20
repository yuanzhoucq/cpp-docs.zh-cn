---
title: "2.6.1 master 构造 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: c092064b-ea57-4d4e-9c99-a004d65656fe
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bff566967749068f9792a98dc3cf2151e4df3d9c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="261-master-construct"></a>2.6.1 master 构造
**Master**指令标识一个构造，用于指定由主线程的团队执行的结构化的块。 语法**master**指令是，如下所示：  
  
```  
#pragma omp master new-linestructured-block  
```  
  
 团队中的其他线程不会执行关联的结构化的块。 在进入或退出 master 构造上的没有隐含的屏障。