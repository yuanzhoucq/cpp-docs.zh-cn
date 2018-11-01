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
ms.openlocfilehash: cf4b7ffb8c6b197dc1c4eea4b6c569e173bb188d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544399"
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

结合使用`_ATLTRY`。 解析为 c + +[捕获 (CAtlException e)](../../cpp/try-throw-and-catch-statements-cpp.md)用于处理给定的类型的 c + + 异常。

##  <a name="_atlcatchall"></a>  _ATLCATCHALL

若要处理发生在关联的错误的语句`_ATLTRY`。

```
_ATLCATCHALL
```

### <a name="remarks"></a>备注

结合使用`_ATLTRY`。 解析为 c + +[自](../../cpp/try-throw-and-catch-statements-cpp.md)用于处理所有类型的 c + + 异常。

##  <a name="_atltry"></a>  _ATLTRY

将标记可能可能发生错误的受保护的代码部分。

```
_ATLTRY
```

### <a name="remarks"></a>备注

结合使用[_ATLCATCH](#_atlcatch)或[_ATLCATCHALL](#_atlcatchall)。 解析为 c + + 符号[尝试](../../cpp/try-throw-and-catch-statements-cpp.md)。

## <a name="see-also"></a>请参阅

[宏](../../atl/reference/atl-macros.md)
