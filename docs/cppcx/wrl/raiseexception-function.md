---
title: RaiseException 函数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
ms.openlocfilehash: 0a1c661378c4b71378456f2813159b7415cf3fad
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784178"
---
# <a name="raiseexception-function"></a>RaiseException 函数

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
inline void __declspec(noreturn)   RaiseException(
      HRESULT hr,
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);
```

### <a name="parameters"></a>参数

*hr*<br/>
异常引发; 异常代码也就是说，操作失败的 HRESULT。

*dwExceptionFlags*<br/>
一个标志，指示持续性异常 （标志值为零） 或 noncontinuable 异常 （标志值为非零）。 默认情况下，例外情况是了不可继续操作。

## <a name="remarks"></a>备注

引发调用线程中的异常。

有关详细信息，请参阅 Windows`RaiseException`函数。

## <a name="requirements"></a>要求

**标头：** internal.h

**命名空间：** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](microsoft-wrl-details-namespace.md)