---
title: "raw_interfaces_only |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: raw_interfaces_only
dev_langs: C++
helpviewer_keywords: raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3cc3588538aea6d1d01cd595b8070950dd474479
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="rawinterfacesonly"></a>raw_interfaces_only
**C + + 专用**  
  
 取消生成的错误处理包装器函数和[属性](../cpp/property-cpp.md)使用这些包装器函数的声明。  
  
## <a name="syntax"></a>语法  
  
```  
raw_interfaces_only  
```  
  
## <a name="remarks"></a>备注  
 `raw_interfaces_only` 特性还会导致移除在命名非属性函数时使用的默认前缀。 通常情况下，该前缀是**raw_**。 如果指定了此特性，函数名将直接来自类型库。  
  
 利用此特性，您可以只公开类型库的低级别内容。  
  
 **结束 c + + 专用**  
  
## <a name="see-also"></a>另请参阅  
 [#import 属性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指令](../preprocessor/hash-import-directive-cpp.md)