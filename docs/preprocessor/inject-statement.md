---
title: "inject_statement |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: inject_statement
dev_langs: C++
helpviewer_keywords: inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6d1ac68cae628f09c9511c4b86eac75da8dff6ec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="injectstatement"></a>inject_statement
**C + + 专用**  
  
 将其自变量作为源文本插入类型库标头。  
  
## <a name="syntax"></a>语法  
  
```  
inject_statement("source_text")  
```  
  
#### <a name="parameters"></a>参数  
 `source_text`  
 要插入类型库标头文件的源文本。  
  
## <a name="remarks"></a>备注  
 该文本放置在用于将类型库内容包装在标头文件中的命名空间声明的开头。  
  
 **结束 c + + 专用**  
  
## <a name="see-also"></a>请参阅  
 [#import 属性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指令](../preprocessor/hash-import-directive-cpp.md)