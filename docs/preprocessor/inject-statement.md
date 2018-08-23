---
title: inject_statement |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- inject_statement
dev_langs:
- C++
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb4142b742ae6c2a758c2a2fb5e09c604959433f
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2018
ms.locfileid: "42541165"
---
# <a name="injectstatement"></a>inject_statement
**C + + 专用**  
  
将其自变量作为源文本插入类型库标头。  
  
## <a name="syntax"></a>语法  
  
```  
inject_statement("source_text")  
```  
  
### <a name="parameters"></a>参数  
*source_text*  
要插入类型库标头文件的源文本。  
  
## <a name="remarks"></a>备注  
 
该文本放置在用于将类型库内容包装在标头文件中的命名空间声明的开头。  
  
**结束 c + + 专用**  
  
## <a name="see-also"></a>请参阅  
 
[#import 属性](../preprocessor/hash-import-attributes-cpp.md)   
[#import 指令](../preprocessor/hash-import-directive-cpp.md)