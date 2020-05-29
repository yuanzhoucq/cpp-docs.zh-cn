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
ms.openlocfilehash: 223f37d7cabbd0b8cd238582773c05d7b9eaabf6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371411"
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
第零个接口 ID。 （必需）

*I1*<br/>
第一个接口 ID。 (可选)

*I2*<br/>
第二个接口 ID。 (可选)

*I3*<br/>
第三个接口 ID。 (可选)

*I4*<br/>
第四个接口 ID。 (可选)

*I5*<br/>
第五个接口 ID。 (可选)

*I6*<br/>
第六个接口 ID。 (可选)

*I7*<br/>
第七个接口 ID。 (可选)

*I8*<br/>
第八个接口 ID。 (可选)

*I9*<br/>
第九个接口 ID。 (可选)

*标志*<br/>
类的配置标志。 在[运行时类标志](runtimeclassflags-structure.md)结构中指定的一个或多个[运行时类类型](runtimeclasstype-enumeration.md)枚举。

## <a name="remarks"></a>备注

派生自 和 的指定接口和实现帮助程序模板`QueryInterface``GetIid`的列表。

每个*I0*到*I9*接口参数`IUnknown`必须`IInspectable`派生自 ，或[链接口](chaininterfaces-structure.md)模板。 *标志*参数确定是否为`IUnknown`或`IInspectable`生成支持。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

| 名称        | 说明                               |
| ----------- | ----------------------------------------- |
| `ClassFlags`| `RuntimeClassFlags<WinRt>` 的同义词。 |

### <a name="protected-methods"></a>受保护的方法

| 名称                                              | 说明                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [实现：：坎卡斯特托](#cancastto)               | 获取指向指定接口的指针。                                                                    |
| [实现：：强制未知](#casttounknown)       | 获取指向基础`IUnknown`接口的指针。                                                        |
| [实现：：用 Iid 填充](#fillarraywithiid) | 将当前零点模板参数指定的接口 ID 插入指定的数组元素。 |

### <a name="protected-constants"></a>受保护的常量

| 名称                              | 说明                                    |
| --------------------------------- | ---------------------------------------------- |
| [实现：：IdCount](#iidcount) | 保存已实现的接口指示数。 |

## <a name="inheritance-hierarchy"></a>继承层次结构

`I0`

`ChainInterfaces`

`I0`

`ImplementsBase`

`ImplementsHelper`

`Implements`

## <a name="requirements"></a>要求

**标题：** 实现.h

**命名空间：** Microsoft::WRL

## <a name="implementscancastto"></a><a name="cancastto"></a>实现：：坎卡斯特托

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

*Ppv*<br/>
如果成功，则指向*riid*指定的接口的指针。

### <a name="return-value"></a>返回值

S_OK如果成功;否则，指示错误的 HRESULT，如E_NOINTERFACE。

### <a name="remarks"></a>备注

这是执行查询接口操作的内部帮助器函数。

## <a name="implementscasttounknown"></a><a name="casttounknown"></a>实现：：强制未知

获取指向基础`IUnknown`接口的指针。

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>返回值

此操作始终成功并返回`IUnknown`指针。

### <a name="remarks"></a>备注

内部帮助器功能。

## <a name="implementsfillarraywithiid"></a><a name="fillarraywithiid"></a>实现：：用 Iid 填充

将当前零点模板参数指定的接口 ID 插入指定的数组元素。

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>参数

*index*<br/>
一个基于零的索引，指示此操作的起始数组元素。 此操作完成后，*索引*将递增 1。

*伊德*<br/>
IID 类型的数组。

### <a name="remarks"></a>备注

内部帮助器功能。

## <a name="implementsiidcount"></a><a name="iidcount"></a>实现：：IdCount

保存已实现的接口指示数。

```cpp
static const unsigned long IidCount;
```
