---
title: 异常处理宏
ms.date: 11/04/2016
f1_keywords:
- atldef/ATL::_ATLCATCH
- atldef/ATL::_ATLCATCHALL
- atldef/ATL::_ATLTRY
helpviewer_keywords:
- exception handling, macros
- C++ exception handling, macros
ms.assetid: a8385d34-3fb0-4006-a42a-de045cacf0f4
ms.openlocfilehash: 8afb2019e38f7548467e85d9a2c1c12c538cf744
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276235"
---
# <a name="exception-handling-macros"></a>异常处理宏

这些宏提供对异常处理支持。

|||
|-|-|
|[_ATLCATCH](#_atlcatch)|若要处理发生在关联的错误的语句`_ATLTRY`。|
|[_ATLCATCHALL](#_atlcatchall)|若要处理发生在关联的错误的语句`_ATLTRY`。|
|[_ATLTRY](#_atltry)|将标记可能可能发生错误的受保护的代码部分。|

## <a name="requirements"></a>要求：

**标头：** atldef.h

##  <a name="_atlcatch"></a>  _ATLCATCH

若要处理发生在关联的错误的语句`_ATLTRY`。

```
_ATLCATCH(e)
```

### <a name="parameters"></a>参数

*e*<br/>
要捕获的异常。

### <a name="remarks"></a>备注

结合使用`_ATLTRY`。 解析为C++[捕获 (CAtlException e)](../../cpp/try-throw-and-catch-statements-cpp.md)用于处理给定的类型的C++异常。

##  <a name="_atlcatchall"></a>  _ATLCATCHALL

若要处理发生在关联的错误的语句`_ATLTRY`。

```
_ATLCATCHALL
```

### <a name="remarks"></a>备注

结合使用`_ATLTRY`。 解析为C++[自](../../cpp/try-throw-and-catch-statements-cpp.md)用于处理所有类型的C++异常。

##  <a name="_atltry"></a>  _ATLTRY

将标记可能可能发生错误的受保护的代码部分。

```
_ATLTRY
```

### <a name="remarks"></a>备注

结合使用[_ATLCATCH](#_atlcatch)或[_ATLCATCHALL](#_atlcatchall)。 解析为C++符号[尝试](../../cpp/try-throw-and-catch-statements-cpp.md)。

## <a name="see-also"></a>请参阅

[宏](../../atl/reference/atl-macros.md)
