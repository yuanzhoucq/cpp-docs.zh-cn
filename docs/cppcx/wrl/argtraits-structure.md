---
title: ArgTraits 结构
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraits
- event/Microsoft::WRL::Details::ArgTraits::args
helpviewer_keywords:
- Microsoft::WRL::Details::ArgTraits structure
- Microsoft::WRL::Details::ArgTraits::args constant
ms.assetid: 58ae4115-c1bc-48c8-b01b-e60554841c30
ms.openlocfilehash: c13e7fec3289b66b40e44f91404a50cba7a473b1
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821709"
---
# <a name="argtraits-structure"></a>ArgTraits 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template<typename TMemberFunction>
struct ArgTraits;

template<typename TDelegateInterface>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(void)>;

template<typename TDelegateInterface, typename TArg1>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1)>;

template<typename TDelegateInterface, typename TArg1, typename TArg2>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8)>;

template<
    typename TDelegateInterface,
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
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8, TArg9)>;
```

### <a name="parameters"></a>参数

*TMemberFunction*<br/>
不能与任何 `Invoke` 方法签名匹配的 ArgTraits 结构的 Typename 参数。

*TDelegateInterface*<br/>
委托接口。

*TArg1*<br/>
`Invoke` 方法的第一个参数的类型。

*TArg2*<br/>
`Invoke` 方法的第二个参数的类型。

*TArg3*<br/>
`Invoke` 方法的第三个参数的类型。

*TArg4*<br/>
`Invoke` 方法的第四个参数的类型。

*TArg5*<br/>
`Invoke` 方法的第五个参数的类型。

*TArg6*<br/>
`Invoke` 方法的第六个参数的类型。

*TArg7*<br/>
`Invoke` 方法的第七个参数的类型。

*TArg8*<br/>
`Invoke` 方法的第八个参数的类型。

*TArg9*<br/>
`Invoke` 方法的第九个参数的类型。

## <a name="remarks"></a>备注

`ArgTraits` 结构声明指定的委托接口和具有指定数量的参数的匿名成员函数。

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公共 Typedef

Name       | 描述
---------- | ----------------------
`Arg1Type` | TArg1 的 typedef。
`Arg2Type` | TArg2 的 typedef。
`Arg3Type` | TArg3 的 typedef。
`Arg4Type` | TArg4 的 typedef。
`Arg5Type` | TArg5 的 typedef。
`Arg6Type` | TArg6 的 typedef。
`Arg7Type` | TArg7 的 typedef。
`Arg8Type` | TArg8 的 typedef。
`Arg9Type` | TArg9 的 typedef。

### <a name="public-constants"></a>公共常量

Name                     | 描述
------------------------ | ---------------------------------------------------------------------------------------
[ArgTraits::args](#args) | 保留委托接口的 `Invoke` 方法的参数数量。

## <a name="inheritance-hierarchy"></a>繼承階層

`ArgTraits`

## <a name="requirements"></a>需求

**标头：** 事件。h

**命名空间：** Microsoft：： WRL：:D etails

## <a name="args"></a>ArgTraits::args

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
static const int args = -1;
```

### <a name="remarks"></a>备注

保留委托接口的 `Invoke` 方法的参数数量。 如果 `args` 等于-1，则不能与 `Invoke` 方法签名匹配。
