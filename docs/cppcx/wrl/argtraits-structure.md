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
ms.openlocfilehash: 16c44d861ebbbc98fa1bffb62a00d1989c0c803c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377162"
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

*T成员功能*<br/>
ArgTraits 结构的类型名称参数，该结构无法与任何`Invoke`方法签名匹配。

*T委托接口*<br/>
委托接口。

*TArg1*<br/>
`Invoke`方法的第一个参数的类型。

*TArg2*<br/>
`Invoke`方法的第二个参数的类型。

*TArg3*<br/>
`Invoke`方法的第三个参数的类型。

*TArg4*<br/>
`Invoke`方法的第四个参数的类型。

*TArg5*<br/>
`Invoke`方法的第五个参数的类型。

*TArg6*<br/>
`Invoke`方法的第六个参数的类型。

*TArg7*<br/>
`Invoke`方法的第七个参数的类型。

*TArg8*<br/>
`Invoke`方法的第八个参数的类型。

*TArg9*<br/>
`Invoke`方法的第九个参数的类型。

## <a name="remarks"></a>备注

结构`ArgTraits`声明指定的委托接口和具有指定数量的参数的匿名成员函数。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称       | 说明
---------- | ----------------------
`Arg1Type` | TArg1 的类型def。
`Arg2Type` | TArg2 的类型def。
`Arg3Type` | TArg3 的类型def。
`Arg4Type` | TArg4 的类型def。
`Arg5Type` | TArg5 的类型def。
`Arg6Type` | TArg6 的类型def。
`Arg7Type` | TArg7 的类型def。
`Arg8Type` | TArg8 的类型def。
`Arg9Type` | TArg9 的类型def。

### <a name="public-constants"></a>公共常量

名称                     | 说明
------------------------ | ---------------------------------------------------------------------------------------
[阿格格茨：阿格茨](#args) | 在委托接口`Invoke`的方法上保留参数数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ArgTraits`

## <a name="requirements"></a>要求

**标题：** 事件.h

**命名空间：** 微软：：WRL：:D

## <a name="argtraitsargs"></a><a name="args"></a>阿格格茨：阿格茨

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
static const int args = -1;
```

### <a name="remarks"></a>备注

在委托接口`Invoke`的方法上保留参数数。 当`args`等于 -1 时，`Invoke`方法签名不能匹配。
