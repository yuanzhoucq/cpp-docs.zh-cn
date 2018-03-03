---
title: "3.1.10 omp_get_nested 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 36b213ee45018e7cc0ccf3a1cb99dcbd640d4457
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="3110-ompgetnested-function"></a>3.1.10 omp_get_nested 函数
`omp_get_nested`如果它处于禁用状态，函数将返回一个非零值，如果启用了嵌套并行机制和 0。 有关嵌套并行的详细信息，请参阅第页 40 页的部分 3.1.9。 格式如下所示：  
  
```  
#include <omp.h>  
int omp_get_nested(void);  
```  
  
 如果实现未实现嵌套并行度，则此函数始终返回 0。