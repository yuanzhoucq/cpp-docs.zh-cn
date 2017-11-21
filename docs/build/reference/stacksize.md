---
title: "STACKSIZE |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: STACKSIZE
dev_langs: C++
helpviewer_keywords: STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 82b33d217e593a35b66bb3530840a739e93082ed
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="stacksize"></a>STACKSIZE
设置堆栈的大小（以字节为单位）。  
  
```  
STACKSIZE reserve[,commit]  
```  
  
## <a name="remarks"></a>备注  
 设置堆栈的等效方法是使用[堆栈分配](../../build/reference/stack-stack-allocations.md)（/ 堆栈） 选项。 请参阅该选项的详细信息上的文档，了解*保留*和`commit`自变量。  
  
 此选项不起在 Dll 上。  
  
## <a name="see-also"></a>另请参阅  
 [模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)