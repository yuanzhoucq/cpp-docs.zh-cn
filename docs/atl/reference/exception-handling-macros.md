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
ms.openlocfilehash: 2beffbbed0efee799005190bd7fd071a2087e4d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330089"
---
# <a name="exception-handling-macros"></a>异常处理宏

这些宏支持异常处理。

|||
|-|-|
|[_ATLCATCH](#_atlcatch)|语句处理关联的`_ATLTRY`中发生的错误。|
|[_ATLCATCHALL](#_atlcatchall)|语句处理关联的`_ATLTRY`中发生的错误。|
|[_ATLTRY](#_atltry)|标记可能发生错误的受保护代码部分。|

## <a name="requirements"></a>要求：

**标题：** atldef.h

## <a name="_atlcatch"></a><a name="_atlcatch"></a>_ATLCATCH

语句处理关联的`_ATLTRY`中发生的错误。

```
_ATLCATCH(e)
```

### <a name="parameters"></a>参数

*e*<br/>
要捕获的异常。

### <a name="remarks"></a>备注

与 一起使用`_ATLTRY`。 解析为处理给定类型的C++异常C++ [catch（CAtlexception e）。](../../cpp/try-throw-and-catch-statements-cpp.md)

## <a name="_atlcatchall"></a><a name="_atlcatchall"></a>_ATLCATCHALL

语句处理关联的`_ATLTRY`中发生的错误。

```
_ATLCATCHALL
```

### <a name="remarks"></a>备注

与 一起使用`_ATLTRY`。 解析为处理所有类型的C++异常C++ [catch（...）。](../../cpp/try-throw-and-catch-statements-cpp.md)

## <a name="_atltry"></a><a name="_atltry"></a>_ATLTRY

标记可能发生错误的受保护代码部分。

```
_ATLTRY
```

### <a name="remarks"></a>备注

与[_ATLCATCH](#_atlcatch)或[_ATLCATCHALL](#_atlcatchall)一起使用。 解析为C++符号[尝试](../../cpp/try-throw-and-catch-statements-cpp.md)。

## <a name="see-also"></a>另请参阅

[宏](../../atl/reference/atl-macros.md)
