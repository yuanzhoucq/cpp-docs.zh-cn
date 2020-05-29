---
title: MakeAndInitialize 函数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAndInitialize
ms.assetid: 71ceeb12-d2a2-4317-b010-3dcde1b39467
ms.openlocfilehash: 28d9e586a766a131e7ab6280859845810c1d9814
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213793"
---
# <a name="makeandinitialize-function"></a>MakeAndInitialize 函数

初始化指定的 Windows 运行时类。 使用此函数实例化在同一模块中定义的组件。

## <a name="syntax"></a>语法

```cpp
template <
    typename T,
    typename I,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8,
    typename TArg9>
HRESULT MakeAndInitialize(
    _Outptr_result_nullonfailure_ I** ppvObject,
    TArg1 &&arg1,
    TArg2 &&arg2,
    TArg3 &&arg3,
    TArg4 &&arg4,
    TArg5 &&arg5,
    TArg6 &&arg6,
    TArg7 &&arg7,
    TArg8 &&arg8,
    TArg9 &&arg9) throw()
```

### <a name="parameters"></a>parameters

*T*<br/>
继承自 `WRL::RuntimeClass`的用户指定的类。

*TArg1*<br/>
传递到指定的运行时类的参数1的类型。

*TArg2*<br/>
传递到指定的运行时类的参数2的类型。

*TArg3*<br/>
传递到指定的运行时类的参数3的类型。

*TArg4*<br/>
传递到指定的运行时类的参数4的类型。

*TArg5*<br/>
传递到指定的运行时类的参数5的类型。

*TArg6*<br/>
传递到指定的运行时类的参数6的类型。

*TArg7*<br/>
传递到指定的运行时类的参数7的类型。

*TArg8*<br/>
传递到指定的运行时类的参数8的类型。

*TArg9*<br/>
传递到指定的运行时类的参数9的类型。

*arg1*<br/>
参数1，传递到指定的运行时类。

*arg2*<br/>
参数2，传递到指定的运行时类。

*arg3*<br/>
参数3，传递到指定的运行时类。

*arg4*<br/>
参数4，传递到指定的运行时类。

*arg5*<br/>
参数5传递到指定的运行时类。

*arg6*<br/>
参数6传递到指定的运行时类。

*arg7*<br/>
传递到指定的运行时类的参数7。

*arg8*<br/>
参数8，传递到指定的运行时类。

*arg9*<br/>
传递到指定的运行时类的参数9。

## <a name="return-value"></a>返回值

HRESULT 值。

## <a name="remarks"></a>备注

有关示例，请参阅[如何：直接实例化 WRL 组件](how-to-instantiate-wrl-components-directly.md)来了解此函数与[MICROSOFT：： WRL：： Make](make-function.md)之间的差异。

## <a name="requirements"></a>要求

**标头：** 实现。h

**命名空间：** Microsoft：： WRL：:D etails

## <a name="see-also"></a>另请参阅

[Microsoft::WRL::Details 命名空间](microsoft-wrl-details-namespace.md)
