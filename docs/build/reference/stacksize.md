---
title: STACKSIZE |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- STACKSIZE
dev_langs:
- C++
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b2093762b3c6f21d319c53a85da5ec5b430a1fd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="stacksize"></a>STACKSIZE
设置堆栈的大小（以字节为单位）。  
  
```  
STACKSIZE reserve[,commit]  
```  
  
## <a name="remarks"></a>备注  
 设置堆栈的等效方法是使用[堆栈分配](../../build/reference/stack-stack-allocations.md)（/ 堆栈） 选项。 请参阅该选项的详细信息上的文档，了解*保留*和`commit`自变量。  
  
 此选项不起在 Dll 上。  
  
## <a name="see-also"></a>请参阅  
 [模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)