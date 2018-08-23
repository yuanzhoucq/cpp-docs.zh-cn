---
title: 2.7.2.4 共享 |Microsoft 文档
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
ms.openlocfilehash: 1de0e32e16d889acb8f1339d783bc194b3508dda
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695689"
---
# <a name="2724-shared"></a>2.7.2.4 shared
此子句共享中出现的变量*变量列表*团队中的所有线程间。 在团队中的所有线程都访问相同的存储区域，以进行**共享**变量。  
  
 语法**共享**子句是，如下所示：  
  
```  
shared(variable-list)  
```