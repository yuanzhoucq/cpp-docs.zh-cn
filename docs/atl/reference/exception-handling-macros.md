---
title: "异常处理宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atldef/ATL::_ATLCATCH
- atldef/ATL::_ATLCATCHALL
- atldef/ATL::_ATLTRY
dev_langs:
- C++
helpviewer_keywords:
- exception handling, macros
- C++ exception handling, macros
ms.assetid: a8385d34-3fb0-4006-a42a-de045cacf0f4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 424a65c44d7bb22d1fef6e21e1892967ecd3e9b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="exception-handling-macros"></a>异常处理宏
这些宏用于异常处理提供支持。  
  
|||  
|-|-|  
|[_ATLCATCH](#_atlcatch)|语句来处理关联中发生的错误`_ATLTRY`。|  
|[_ATLCATCHALL](#_atlcatchall)|语句来处理关联中发生的错误`_ATLTRY`。|  
|[_ATLTRY](#_atltry)|将可能会出错无法一受保护的代码段的标记。|  
  
## <a name="requirements"></a>要求：
**标头：** atldef.h

##  <a name="_atlcatch"></a>_ATLCATCH  
 语句来处理关联中发生的错误`_ATLTRY`。  
  
```
_ATLCATCH(e)
```  
  
### <a name="parameters"></a>参数  
 *e*  
 要捕获的异常。  
  
### <a name="remarks"></a>备注  
 结合使用`_ATLTRY`。 解析为 c + +[捕获 (CAtlException e)](../../cpp/try-throw-and-catch-statements-cpp.md)处理给定的类型的 c + + 异常。  
  
##  <a name="_atlcatchall"></a>_ATLCATCHALL  
 语句来处理关联中发生的错误`_ATLTRY`。  
  
```
_ATLCATCHALL
```  
  
### <a name="remarks"></a>备注  
 结合使用`_ATLTRY`。 解析为 c + +[之后](../../cpp/try-throw-and-catch-statements-cpp.md)处理所有类型的 c + + 异常。  
  
##  <a name="_atltry"></a>_ATLTRY  
 将可能会出错无法一受保护的代码段的标记。  
  
```
_ATLTRY
```  
  
### <a name="remarks"></a>备注  
 结合使用[_ATLCATCH](#_atlcatch)或[_ATLCATCHALL](#_atlcatchall)。 解析为 c + + 符号[重](../../cpp/try-throw-and-catch-statements-cpp.md)。  
  
## <a name="see-also"></a>请参阅  
 [宏](../../atl/reference/atl-macros.md)
