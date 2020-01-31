---
title: Implements 结构
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements
- implements/Microsoft::WRL::Implements::CanCastTo
- implements/Microsoft::WRL::Implements::CastToUnknown
- implements/Microsoft::WRL::Implements::FillArrayWithIid
- implements/Microsoft::WRL::Implements::IidCount
helpviewer_keywords:
- Microsoft::WRL::Implements structure
- Microsoft::WRL::Implements::CanCastTo method
- Microsoft::WRL::Implements::CastToUnknown method
- Microsoft::WRL::Implements::FillArrayWithIid method
- Microsoft::WRL::Implements::IidCount method
ms.assetid: 29b13e90-34d4-4a0b-babd-5187c9eb0c36
ms.openlocfilehash: 0ce6e9193107cbd0d033d99b257e41004b4343a8
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821852"
---
# <a name="implements-structure"></a>Implements 结构

为指定的接口实现 `QueryInterface` 和 `GetIid`。

## <a name="syntax"></a>语法

```cpp
template <
    typename I0,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil,
    typename I3 = Details::Nil,
    typename I4 = Details::Nil,
    typename I5 = Details::Nil,
    typename I6 = Details::Nil,
    typename I7 = Details::Nil,
    typename I8 = Details::Nil,
    typename I9 = Details::Nil
>
struct __declspec(novtable) Implements :
    Details::ImplementsHelper<
        RuntimeClassFlags<WinRt>,
        typename Details::InterfaceListHelper<
            I0, I1, I2, I3, I4, I5, I6, I7, I8, I9
        >::TypeT
    >,
    Details::ImplementsBase;

template <
    int flags,
    typename I0,
    typename I1,
    typename I2,
    typename I3,
    typename I4,
    typename I5,
    typename I6,
    typename I7,
    typename I8
>
struct __declspec(novtable) Implements<
        RuntimeClassFlags<flags>,
        I0, I1, I2, I3, I4, I5, I6, I7, I8> :
    Details::ImplementsHelper<
        RuntimeClassFlags<flags>,
        typename Details::InterfaceListHelper<
            I0, I1, I2, I3, I4, I5, I6, I7, I8
        >::TypeT
    >,
    Details::ImplementsBase;
```

### <a name="parameters"></a>参数

*I0*<br/>
第零个接口 ID。 必需

*I1*<br/>
第一个接口 ID。 （可选）

*I2*<br/>
第二个接口 ID。 （可选）

*I3*<br/>
第三个接口 ID。 （可选）

*I4*<br/>
第四个接口 ID。 （可选）

*I5*<br/>
第五个接口 ID。 （可选）

*I6*<br/>
第六个接口 ID。 （可选）

*I7*<br/>
第七个接口 ID。 （可选）

*I8*<br/>
第八个接口 ID。 （可选）

*I9*<br/>
第九个接口 ID。 （可选）

*flags*<br/>
类的配置标志。 [RuntimeClassFlags](runtimeclassflags-structure.md)结构中指定的一个或多个[RuntimeClassType](runtimeclasstype-enumeration.md)枚举。

## <a name="remarks"></a>备注

派生自指定接口的列表并实现 `QueryInterface` 和 `GetIid`的帮助器模板。

每个*I0*到*I9*接口参数都必须派生自 `IUnknown`、`IInspectable`或[ChainInterfaces](chaininterfaces-structure.md)模板。 *Flags*参数确定是否为 `IUnknown` 或 `IInspectable`生成支持。

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公共 Typedef

| Name        | 描述                               |
| ----------- | ----------------------------------------- |
| `ClassFlags`| `RuntimeClassFlags<WinRt>` 的同义词。 |

### <a name="protected-methods"></a>受保護的方法

| Name                                              | 描述                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Implements::CanCastTo](#cancastto)               | 获取指向指定接口的指针。                                                                    |
| [Implements：： CastToUnknown](#casttounknown)       | 获取指向基础 `IUnknown` 接口的指针。                                                        |
| [Implements::FillArrayWithIid](#fillarraywithiid) | 将当前第零个模板参数指定的接口 ID 插入指定的数组元素。 |

### <a name="protected-constants"></a>受保护常量

| Name                              | 描述                                    |
| --------------------------------- | ---------------------------------------------- |
| [Implements::IidCount](#iidcount) | 保留已实现的接口 Id 的数量。 |

## <a name="inheritance-hierarchy"></a>繼承階層

`I0`

`ChainInterfaces`

`I0`

`ImplementsBase`

`ImplementsHelper`

`Implements`

## <a name="requirements"></a>需求

**标头：** 实现。h

**命名空间：** Microsoft::WRL

## <a name="cancastto"></a>Implements：： CanCastTo

获取指向指定接口的指针。

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>参数

*riid*<br/>
对接口 ID 的引用。

*ppv*<br/>
如果成功，则为由*riid*指定的接口的指针。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK;否则，为指示错误的 HRESULT，如 E_NOINTERFACE。

### <a name="remarks"></a>备注

这是执行 QueryInterface 操作的内部 helper 函数。

## <a name="casttounknown"></a>Implements：： CastToUnknown

获取指向基础 `IUnknown` 接口的指针。

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>返回值

此操作始终成功并返回 `IUnknown` 指针。

### <a name="remarks"></a>备注

内部 helper 函数。

## <a name="fillarraywithiid"></a>Implements::FillArrayWithIid

将当前第零个模板参数指定的接口 ID 插入指定的数组元素。

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>参数

*index*<br/>
从零开始的索引，它指示此操作的起始数组元素。 此操作完成后，*索引*将递增1。

*iid*<br/>
类型为 IID 的数组。

### <a name="remarks"></a>备注

内部 helper 函数。

## <a name="iidcount"></a>Implements::IidCount

保留已实现的接口 Id 的数量。

```cpp
static const unsigned long IidCount;
```
