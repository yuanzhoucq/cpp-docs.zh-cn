---
title: CComPtrBase 类
ms.date: 11/04/2016
f1_keywords:
- CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase::Advise
- ATLCOMCLI/ATL::CComPtrBase::Attach
- ATLCOMCLI/ATL::CComPtrBase::CoCreateInstance
- ATLCOMCLI/ATL::CComPtrBase::CopyTo
- ATLCOMCLI/ATL::CComPtrBase::Detach
- ATLCOMCLI/ATL::CComPtrBase::IsEqualObject
- ATLCOMCLI/ATL::CComPtrBase::QueryInterface
- ATLCOMCLI/ATL::CComPtrBase::Release
- ATLCOMCLI/ATL::CComPtrBase::SetSite
- ATLCOMCLI/ATL::CComPtrBase::p
helpviewer_keywords:
- CComPtrBase class
ms.assetid: 6dbe9543-dee8-4a97-b02f-dd3a25f4a1a0
ms.openlocfilehash: 9c62cc912b3fea3ea68390882bdda37cbfb25a7e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747757"
---
# <a name="ccomptrbase-class"></a>CComPtrBase 类

此类为使用基于 COM 的内存例程的智能指针类提供了基础。

## <a name="syntax"></a>语法

```
template <class T>
class CComPtrBase
```

#### <a name="parameters"></a>参数

*T*<br/>
要由智能指针引用的对象类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComPtrBase：*CComPtrBase](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComPtrBase：建议](#advise)|调用此方法以在`CComPtrBase`连接点和客户端的接收器之间创建连接。|
|[CComPtrBase：附加](#attach)|调用此方法以获取现有指针的所有权。|
|[CComPtrBase：：共同创建实例](#cocreateinstance)|调用此方法以创建与指定的类 ID 或程序 ID 关联的类的对象。|
|[CComptrBase：：复制到](#copyto)|调用此方法以将`CComPtrBase`指针复制到另一个指针变量。|
|[CComPtrBase：:D](#detach)|调用此方法以释放指针的所有权。|
|[CComPtrBase：是等价物](#isequalobject)|调用此方法以检查指定`IUnknown`点是否指向与`CComPtrBase`对象关联的同一对象。|
|[CComPtrBase：查询接口](#queryinterface)|调用此方法以返回指向指定接口的指针。|
|[CComPtrBase：发布](#release)|调用此方法以释放接口。|
|[CComPtrBase：设置网站](#setsite)|调用此方法将`CComPtrBase`对象的站点设置为`IUnknown`父对象的站点。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CComPtrBase：：运算符 T*](#operator_t_star)|强制转换运算符。|
|[CComPtrBase：操作员！](#operator_not)|NOT 运算符。|
|[CComPtrBase：：操作员&](#operator_amp)|& 运算符。|
|[CComPtrBase：操作员 |](#operator_star)|\* 运算符。|
|[CComPtrBase：：操作员<](#ccomptrbase__operator lt)|小于运算符。|
|[CComPtrBase：运算符 |](#operator_eq_eq)|相等运算符。|
|[CComPtrBase：运算符 ->](#operator_ptr)|指向成员的指针运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CComPtrBase：:p](#p)|指针数据成员变量。|

## <a name="remarks"></a>备注

此类为使用 COM 内存管理例程的其他智能指针（如[CComQIPtr](../../atl/reference/ccomqiptr-class.md)和[CComPtr）](../../atl/reference/ccomptr-class.md)提供了基础。 派生类添加自己的构造函数和运算符，但依赖于 提供`CComPtrBase`的方法。

## <a name="requirements"></a>要求

**标题：** atlcomcli.h

## <a name="ccomptrbaseadvise"></a><a name="advise"></a>CComPtrBase：建议

调用此方法以在`CComPtrBase`连接点和客户端的接收器之间创建连接。

```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```

### <a name="parameters"></a>参数

*朋 克*<br/>
指向客户端的`IUnknown`指针。

*Iid*<br/>
连接点的 GUID。 通常，这与连接点管理的传出接口相同。

*pdw*<br/>
指向唯一标识连接的 Cookie 的指针。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

有关详细信息[，请参阅 Atl 建议](connection-point-global-functions.md#atladvise)。

## <a name="ccomptrbaseattach"></a><a name="attach"></a>CComPtrBase：附加

调用此方法以获取现有指针的所有权。

```cpp
void Attach(T* p2) throw();
```

### <a name="parameters"></a>参数

*p2*<br/>
该`CComPtrBase`对象将取得此指针的所有权。

### <a name="remarks"></a>备注

`Attach`调用[CComPtrBase：：释放](#release)现有[CComPtrBase：:p](#p)成员变量，然后将*p2*分配给`CComPtrBase::p`。 当对象`CComPtrBase`取得指针的所有权时，它将自动调用`Release`指针，如果对象的引用计数变为 0，该指针将删除指针和任何已分配的数据。

## <a name="ccomptrbaseccomptrbase"></a><a name="dtor"></a>CComPtrBase：*CComPtrBase

析构函数。

```
~CComPtrBase() throw();
```

### <a name="remarks"></a>备注

释放 所指向的`CComPtrBase`接口。

## <a name="ccomptrbasecocreateinstance"></a><a name="cocreateinstance"></a>CComPtrBase：：共同创建实例

调用此方法以创建与指定的类 ID 或程序 ID 关联的类的对象。

```
HRESULT CoCreateInstance(
    LPCOLESTR szProgID,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();

HRESULT CoCreateInstance(
    REFCLSID rclsid,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();
```

### <a name="parameters"></a>参数

*szProgID*<br/>
指向 ProgID 的指针，用于恢复 CLSID。

*pUnkOuter*<br/>
如果 NULL，则指示对象不是作为聚合的一部分创建的。 如果非 NULL，则是指向聚合对象的接口（控制`IUnknown``IUnknown`） 的指针。

*dwCls上下文*<br/>
管理新创建对象的代码将在其中运行的上下文。

*rclsid*<br/>
与将用于创建对象的数据和代码关联的 CLSID。

### <a name="return-value"></a>返回值

返回S_OK成功，或REGDB_E_CLASSNOTREG，CLASS_E_NOAGGREGATION，CO_E_CLASSSTRING或E_NOINTERFACE失败。 有关这些错误的说明，请参阅[CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)和[CLSIDFromProgID。](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid)

### <a name="remarks"></a>备注

如果调用方法的第一种形式，[则 CLSIDFromProgID](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid)用于恢复 CLSID。 然后，两个窗体调用[CoCreateClassinstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)。

在调试生成中，如果[CComPtrBase：:p](#p)不等于 NULL，则会发生断言错误。

## <a name="ccomptrbasecopyto"></a><a name="copyto"></a>CComptrBase：：复制到

调用此方法以将`CComPtrBase`指针复制到另一个指针变量。

```
HRESULT CopyTo(T** ppT) throw();
```

### <a name="parameters"></a>参数

*Ppt*<br/>
将接收指针的变量的地址`CComPtrBase`。

### <a name="return-value"></a>返回值

返回S_OK成功，E_POINTER失败。

### <a name="remarks"></a>备注

将`CComPtrBase`指针复制到*ppT*。 [CComPtrBase：:p](#p)成员变量上的引用计数递增。

如果*ppT*等于 NULL，则将返回错误 HRESULT。 在调试生成中，如果*ppT*等于 NULL，则会发生断言错误。

## <a name="ccomptrbasedetach"></a><a name="detach"></a>CComPtrBase：:D

调用此方法以释放指针的所有权。

```
T* Detach() throw();
```

### <a name="return-value"></a>返回值

返回指针的副本。

### <a name="remarks"></a>备注

释放指针的所有权，将[CComPtrBase：:p](#p)数据成员变量设置为 NULL，并返回指针的副本。

## <a name="ccomptrbaseisequalobject"></a><a name="isequalobject"></a>CComPtrBase：是等价物

调用此方法以检查指定`IUnknown`点是否指向与`CComPtrBase`对象关联的同一对象。

```
bool IsEqualObject(IUnknown* pOther) throw();
```

### <a name="parameters"></a>参数

*p其他*<br/>
要比较的 `IUnknown *`。

### <a name="return-value"></a>返回值

如果对象相同，则返回 true，否则为 false。

## <a name="ccomptrbaseoperator-"></a><a name="operator_not"></a>CComPtrBase：操作员！

NOT 运算符。

```
bool operator!() const throw();
```

### <a name="return-value"></a>返回值

如果指针等于`CComHeapPtr`NULL，则返回 true，否则为 false。

## <a name="ccomptrbaseoperator-amp"></a><a name="operator_amp"></a>CComPtrBase：：运算符&amp;

& 运算符。

```
T** operator&() throw();
```

### <a name="return-value"></a>返回值

返回对象指向的对象的地址`CComPtrBase`。

## <a name="ccomptrbaseoperator-"></a><a name="operator_star"></a>CComPtrBase：：运算符\*

\* 运算符。

```
T& operator*() const throw();
```

### <a name="return-value"></a>返回值

返回[CComPtrBase：:p](#p)的值。即指向对象引用的对象的`CComPtrBase`指针。

如果调试生成，如果[CComPtrBase：:p](#p)不等于 NULL，则会发生断言错误。

## <a name="ccomptrbaseoperator-"></a><a name="operator_eq_eq"></a>CComPtrBase：运算符 |

相等运算符。

```
bool operator== (T* pT) const throw();
```

### <a name="parameters"></a>参数

*铂*<br/>
指向对象的指针。

### <a name="return-value"></a>返回值

如果`CComPtrBase`和*pT*指向同一对象，则返回 true，否则为 false。

## <a name="ccomptrbaseoperator--gt"></a><a name="operator_ptr"></a>CComPtrBase：运算符 -&gt;

指针到成员运算符。

```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```

### <a name="return-value"></a>返回值

返回[CComPtrBase：:p](#p)数据成员变量的值。

### <a name="remarks"></a>备注

使用此运算符调用`CComPtrBase`对象指向的类中的方法。 在调试生成中，如果数据成员指向 NULL，`CComPtrBase`则会发生断言失败。

## <a name="ccomptrbaseoperator-lt"></a><a name="operator_lt"></a>CComPtrBase：：运算符&lt;

小于运算符。

```
bool operator<(T* pT) const throw();
```

### <a name="parameters"></a>参数

*铂*<br/>
指向对象的指针。

### <a name="return-value"></a>返回值

如果当前对象管理的指针小于要比较它的指针，则返回 true。

## <a name="ccomptrbaseoperator-t"></a><a name="operator_t_star"></a>CComPtrBase：：运算符 T\*

强制转换运算符。

```
operator T*() const throw();
```

### <a name="remarks"></a>备注

返回指向类模板中定义的对象数据类型的指针。

## <a name="ccomptrbasep"></a><a name="p"></a>CComPtrBase：:p

指针数据成员变量。

```
T* p;
```

### <a name="remarks"></a>备注

此成员变量保存指针信息。

## <a name="ccomptrbasequeryinterface"></a><a name="queryinterface"></a>CComPtrBase：查询接口

调用此方法以返回指向指定接口的指针。

```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```

### <a name="parameters"></a>参数

*问*<br/>
需要接口指针的对象类型。

*Pp*<br/>
接收请求的接口指针的输出变量的地址。

### <a name="return-value"></a>返回值

返回S_OK成功，或E_NOINTERFACE失败。

### <a name="remarks"></a>备注

此方法调用[I 未知：查询接口](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))。

在调试生成中，如果*pp*不等于 NULL，则会发生断言错误。

## <a name="ccomptrbaserelease"></a><a name="release"></a>CComPtrBase：发布

调用此方法以释放接口。

```cpp
void Release() throw();
```

### <a name="remarks"></a>备注

接口被释放[，CComPtrBase：:p](#p)设置为 NULL。

## <a name="ccomptrbasesetsite"></a><a name="setsite"></a>CComPtrBase：设置网站

调用此方法将`CComPtrBase`对象的站点设置为`IUnknown`父对象的站点。

```
HRESULT SetSite(IUnknown* punkParent) throw();
```

### <a name="parameters"></a>参数

*朋克家长*<br/>
指向父级`IUnknown`接口的指针。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

此方法调用[AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite)。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
