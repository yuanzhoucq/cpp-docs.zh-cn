---
title: raw_dispinterfaces |Microsoft 文档
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
ms.openlocfilehash: 1f2a0d91d0f0dd3d23886ade75072526e6c895f7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849449"
---
# <a name="rawdispinterfaces"></a>raw_dispinterfaces
**C + + 专用**  
  
 告知编译器生成低级别的包装器函数的调度接口方法和属性，调用**idispatch:: Invoke**并返回`HRESULT`错误代码。  
  
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