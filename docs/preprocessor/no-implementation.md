---
title: no_implementation |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_implementation
dev_langs:
- C++
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbf715e2cbd19d139904438e722e4d0b72e29f29
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2018
ms.locfileid: "42541170"
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
  
结合使用此特性[implementation_only](../preprocessor/implementation-only.md)。  
  
**结束 c + + 专用**  
  
## <a name="see-also"></a>请参阅  
 
[#import 属性](../preprocessor/hash-import-attributes-cpp.md)   
[#import 指令](../preprocessor/hash-import-directive-cpp.md)