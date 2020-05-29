---
title: Make 函数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Make
helpviewer_keywords:
- Make function
ms.assetid: 66704143-df99-4a95-904d-ed99607e1034
ms.openlocfilehash: ffd0967b741475b260eef80ec24d56874a6bcb1f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213806"
---
# <a name="make-function"></a>Make 函数

初始化指定的 Windows 运行时类。 使用此函数实例化在同一模块中定义的组件。

## <a name="syntax"></a>语法

```cpp
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8,
   typename TArg9
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7,
   TArg8 &&arg8,
   TArg9 &&arg9
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7,
   TArg8 &&arg8
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3
);
template <
   typename T,
   typename TArg1,
   typename TArg2
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2
);
template <
   typename T,
   typename TArg1
>
ComPtr<T> Make(
   TArg1 &&arg1
);
template <
   typename T
>
ComPtr<T> Make();
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

如果成功，则为 `ComPtr<T>` 对象;否则，`nullptr`。

## <a name="remarks"></a>备注

有关示例，请参阅[如何：直接实例化 WRL 组件](how-to-instantiate-wrl-components-directly.md)来了解此函数与[MICROSOFT：： WRL：:D Etails：： MakeAndInitialize](makeandinitialize-function.md)之间的差异。

## <a name="requirements"></a>要求

**标头：** 实现。h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>另请参阅

[Microsoft::WRL Namespace](microsoft-wrl-namespace.md)
