---
title: raw_interfaces_only |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_interfaces_only
dev_langs:
- C++
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63097c9ac47f3b791ff7fd5949cece4d85e5ca1f
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2018
ms.locfileid: "42538588"
---
# <a name="rawinterfacesonly"></a>raw_interfaces_only
**C + + 专用**  
  
取消生成的错误处理的包装函数和[属性](../cpp/property-cpp.md)使用这些包装器函数的声明。  
  
## <a name="syntax"></a>语法  
  
```  
raw_interfaces_only  
```  
  
## <a name="remarks"></a>备注  
 
**Raw_interfaces_only**属性还会导致命名要删除的非属性函数中使用的默认前缀。 通常情况下，该前缀是**raw_**。 如果指定了此特性，函数名将直接来自类型库。  
  
利用此特性，您可以只公开类型库的低级别内容。  
  
**结束 c + + 专用**  
  
## <a name="see-also"></a>请参阅  
 
[#import 属性](../preprocessor/hash-import-attributes-cpp.md)   
[#import 指令](../preprocessor/hash-import-directive-cpp.md)