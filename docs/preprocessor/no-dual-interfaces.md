---
title: "no_dual_interfaces |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: no_dual_interfaces
dev_langs: C++
helpviewer_keywords: no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 42501c329b5c040f762b692e9298b184a2035d7d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="nodualinterfaces"></a>no_dual_interfaces
**C + + 专用**  
  
 更改编译器为双重接口方法生成包装器函数的方式。  
  
## <a name="syntax"></a>语法  
  
```  
no_dual_interfaces  
```  
  
## <a name="remarks"></a>备注  
 通常，该包装器将通过接口的虚函数表调用方法。 与`no_dual_interfaces`，改为调用包装**idispatch:: Invoke**来调用的方法。  
  
 **结束 c + + 专用**  
  
## <a name="see-also"></a>请参阅  
 [#import 属性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指令](../preprocessor/hash-import-directive-cpp.md)