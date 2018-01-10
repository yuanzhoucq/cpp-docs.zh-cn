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
ms.workload: cplusplus
ms.openlocfilehash: 2517e19b49f1314e7432bb265756193ea3bb8f91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="261-master-construct"></a>2.6.1 master 构造
**Master**指令标识一个构造，用于指定由主线程的团队执行的结构化的块。 语法**master**指令是，如下所示：  
  
```  
#pragma omp master new-linestructured-block  
```  
  
 团队中的其他线程不会执行关联的结构化的块。 在进入或退出 master 构造上的没有隐含的屏障。