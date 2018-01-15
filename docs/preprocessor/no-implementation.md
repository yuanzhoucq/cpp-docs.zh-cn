---
title: "no_implementation |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: no_implementation
dev_langs: C++
helpviewer_keywords: no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aa0a8337de519b2b0d43e8d5035e3845e1aefbe4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="noimplementation"></a>no_implementation
**C + + 专用**  
  
 取消生成 .tli 标头，它包含包装器成员函数的实现。  
  
## <a name="syntax"></a>语法  
  
```  
no_implementation  
```  
  
## <a name="remarks"></a>备注  
 如果指定此特性，则将生成 .tlh 标头（带用于公开类型库项的声明），而无需用于包含 .tli 标头文件的 `#include` 语句。  
  
 结合使用此属性[implementation_only](../preprocessor/implementation-only.md)。  
  
 **结束 c + + 专用**  
  
## <a name="see-also"></a>请参阅  
 [#import 属性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指令](../preprocessor/hash-import-directive-cpp.md)