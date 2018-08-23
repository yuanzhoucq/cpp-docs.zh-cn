---
title: raw_dispinterfaces |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_dispinterfaces
dev_langs:
- C++
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 093c994de24b947c53bfc19d33213e77f3ec2593
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2018
ms.locfileid: "42539746"
---
# <a name="rawdispinterfaces"></a>raw_dispinterfaces
**C + + 专用**  
  
告知编译器生成低级别的包装函数的调用调度接口方法和属性的`IDispatch::Invoke`并返回 HRESULT 错误代码。  
  
## <a name="syntax"></a>语法  
  
```  
raw_dispinterfaces  
```  
  
## <a name="remarks"></a>备注  
 
如果未指定该特性，则只生成高级包装器，它在失败时引发 C++ 异常。  
  
**结束 c + + 专用**  
  
## <a name="see-also"></a>请参阅  
 
[#import 属性](../preprocessor/hash-import-attributes-cpp.md)   
[#import 指令](../preprocessor/hash-import-directive-cpp.md)