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
ms.openlocfilehash: 63cac6931428644cc5ddec7d87e49007e95e039d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58784202"
---
# <a name="implements-structure"></a>Implements 结构

实现`QueryInterface`和`GetIid`指定接口。

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
第零个接口 id。 （必需）

*I1*<br/>
第一个接口 id。 （可选）

*I2*<br/>
第二个接口 id。 （可选）

*I3*<br/>
第三个接口 id。 （可选）

*I4*<br/>
第四个接口 id。 （可选）

*I5*<br/>
第五个接口 id。 （可选）

*I6*<br/>
第六个接口 id。 （可选）

*I7*<br/>
第七个接口 id。 （可选）

*I8*<br/>
第八个接口 id。 （可选）

*I9*<br/>
第九个接口 id。 （可选）

*flags*<br/>
配置标志的类。 一个或多个[RuntimeClassType](runtimeclasstype-enumeration.md)中指定的枚举[RuntimeClassFlags](runtimeclassflags-structure.md)结构。

## <a name="remarks"></a>备注

派生的指定接口的列表，它实现的帮助程序模板用于`QueryInterface`和`GetIid`。

每个*I0*通过*I9*接口参数必须或者派生`IUnknown`， `IInspectable`，或者[ChainInterfaces](chaininterfaces-structure.md)模板。 *标志*参数确定是否为生成支持`IUnknown`或`IInspectable`。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

| 名称        | 描述                               |
| ----------- | ----------------------------------------- |
| `ClassFlags`| `RuntimeClassFlags<WinRt>` 的同义词。 |

### <a name="protected-methods"></a>受保护的方法

| 名称                                              | 描述                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Implements::CanCastTo](#cancastto)               | 获取一个指向指定接口。                                                                    |
| [Implements::CastToUnknown](#casttounknown)       | 获取一个指针指向基础`IUnknown`接口。                                                        |
| [Implements::FillArrayWithIid](#fillarraywithiid) | 将插入到指定的数组元素指定由当前第零个模板参数的接口 ID。 |

### <a name="protected-constants"></a>受保护的常量

| 名称                              | 描述                                    |
| --------------------------------- | ---------------------------------------------- |
| [Implements::IidCount](#iidcount) | 存储实现的接口 Id 的数目。 |

## <a name="inheritance-hierarchy"></a>继承层次结构

`I0`

`ChainInterfaces`

`I0`

`ImplementsBase`

`ImplementsHelper`

`Implements`

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft:: wrl

## <a name="cancastto"></a>Implements::CanCastTo

获取一个指向指定接口。

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>参数

*riid*<br/>
对接口 id。

*ppv*<br/>
如果成功，指向接口由指定*riid*。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为一个 HRESULT，指示错误，例如 E_NOINTERFACE。

### <a name="remarks"></a>备注

这是执行 QueryInterface 操作内部帮助器函数。

## <a name="casttounknown"></a>Implements::CastToUnknown

获取一个指针指向基础`IUnknown`接口。

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>返回值

此操作始终成功并返回`IUnknown`指针。

### <a name="remarks"></a>备注

内部帮助器函数。

## <a name="fillarraywithiid"></a>Implements::FillArrayWithIid

将插入到指定的数组元素指定由当前第零个模板参数的接口 ID。

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>参数

*index*<br/>
一个从零开始的索引，该值指示此操作的起始数组元素。 此操作完成后，*索引*都会增加 1。

*iids*<br/>
类型 IID 的数组。

### <a name="remarks"></a>备注

内部帮助器函数。

## <a name="iidcount"></a>Implements::IidCount

存储实现的接口 Id 的数目。

```cpp
static const unsigned long IidCount;
```
