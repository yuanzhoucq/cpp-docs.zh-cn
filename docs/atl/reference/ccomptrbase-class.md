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
ms.openlocfilehash: 5bb599b88671447e219421efacac7a2d8a5f7b06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246226"
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
要引用的智能指针的对象类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComPtrBase:: ~ CComPtrBase](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComPtrBase::Advise](#advise)|调用此方法以之间创建连接`CComPtrBase`的连接点和客户端的接收器。|
|[CComPtrBase::Attach](#attach)|调用此方法以获取现有指针的所有权。|
|[CComPtrBase::CoCreateInstance](#cocreateinstance)|调用此方法以创建与指定的类 ID 或计划 id。 关联的类的对象|
|[CComPtrBase::CopyTo](#copyto)|调用此方法来复制`CComPtrBase`到另一个指针变量的指针。|
|[CComPtrBase::Detach](#detach)|调用此方法释放的指针的所有权。|
|[CComPtrBase::IsEqualObject](#isequalobject)|调用此方法来检查是否指定`IUnknown`指向与关联的相同对象`CComPtrBase`对象。|
|[CComPtrBase::QueryInterface](#queryinterface)|调用此方法以返回指向指定接口的指针。|
|[CComPtrBase::Release](#release)|调用此方法释放该接口。|
|[CComPtrBase::SetSite](#setsite)|调用此方法以设置的站点`CComPtrBase`对象传递给`IUnknown`的父对象。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CComPtrBase::operator T *](#operator_t_star)|强制转换运算符。|
|[CComPtrBase::operator ！](#operator_not)|NOT 运算符。|
|[CComPtrBase::operator （& a)](#operator_amp)|& 运算符。|
|[CComPtrBase::operator *](#operator_star)|\* 运算符。|
|[CComPtrBase::operator <](#ccomptrbase__operator lt)|小于-运算符。|
|[CComPtrBase::operator = =](#operator_eq_eq)|相等运算符。|
|[CComPtrBase::operator->](#operator_ptr)|指针到成员运算符中。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CComPtrBase::p](#p)|指针数据成员变量。|

## <a name="remarks"></a>备注

此类提供其他智能指针的使用 COM 内存管理例程，如下所示的基础[CComQIPtr](../../atl/reference/ccomqiptr-class.md)并[CComPtr](../../atl/reference/ccomptr-class.md)。 派生的类中添加其自己的构造函数和运算符，但依赖于提供的方法`CComPtrBase`。

## <a name="requirements"></a>要求

**标头：** atlcomcli.h

##  <a name="advise"></a>  CComPtrBase::Advise

调用此方法以之间创建连接`CComPtrBase`的连接点和客户端的接收器。

```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```

### <a name="parameters"></a>参数

*pUnk*<br/>
指向客户端的`IUnknown`。

*iid*<br/>
连接点的 GUID。 通常情况下，这是与连接点管理输出接口相同。

*pdw*<br/>
一个指向唯一标识连接的 cookie。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

请参阅[AtlAdvise](connection-point-global-functions.md#atladvise)有关详细信息。

##  <a name="attach"></a>  CComPtrBase::Attach

调用此方法以获取现有指针的所有权。

```
void Attach(T* p2) throw();
```

### <a name="parameters"></a>参数

*p2*<br/>
`CComPtrBase`对象将获得 this 指针的所有权。

### <a name="remarks"></a>备注

`Attach` 调用[CComPtrBase::Release](#release)针对现有[CComPtrBase::p](#p)成员变量，然后分配*p2*到`CComPtrBase::p`。 当`CComPtrBase`对象采用的指针的所有权，它将自动调用`Release`如果该对象的引用计数变为 0，则这将删除指针和任何指针分配数据。

##  <a name="dtor"></a>  CComPtrBase:: ~ CComPtrBase

析构函数。

```
~CComPtrBase() throw();
```

### <a name="remarks"></a>备注

释放由指向接口`CComPtrBase`。

##  <a name="cocreateinstance"></a>  CComPtrBase::CoCreateInstance

调用此方法以创建与指定的类 ID 或计划 id。 关联的类的对象

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
指向 ProgID，用来恢复 CLSID 的指针。

*pUnkOuter*<br/>
如果为 NULL，指示不创建对象的聚合的一部分。 如果非 NULL 是指向聚合对象的指针`IUnknown`接口 (控制`IUnknown`)。

*dwClsContext*<br/>
管理新创建的对象的代码将在其中运行的上下文。

*rclsid*<br/>
与数据和将用于创建对象的代码相关联的 CLSID。

### <a name="return-value"></a>返回值

在失败时返回成功，或 REGDB_E_CLASSNOTREG、 CLASS_E_NOAGGREGATION、 CO_E_CLASSSTRING 或 E_NOINTERFACE，则为 S_OK。 请参阅[CoCreateClassInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance)并[CLSIDFromProgID](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromprogid)有关这些错误的说明。

### <a name="remarks"></a>备注

如果调用方法的第一种形式，则[CLSIDFromProgID](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromprogid)用于恢复 CLSID。 然后调用这两个窗体[CoCreateClassInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance)。

在调试版本中，如果出现断言错误[CComPtrBase::p](#p)不等于 NULL。

##  <a name="copyto"></a>  CComPtrBase::CopyTo

调用此方法来复制`CComPtrBase`到另一个指针变量的指针。

```
HRESULT CopyTo(T** ppT) throw();
```

### <a name="parameters"></a>参数

*ppT*<br/>
将接收变量的地址`CComPtrBase`指针。

### <a name="return-value"></a>返回值

如果成功，E_POINTER 失败时返回 S_OK。

### <a name="remarks"></a>备注

副本`CComPtrBase`指针，指向*ppT*。 上的引用计数[CComPtrBase::p](#p)成员变量将递增。

如果将返回的 HRESULT 错误*ppT*等于 NULL。 在调试版本中，如果出现断言错误*ppT*等于 NULL。

##  <a name="detach"></a>  CComPtrBase::Detach

调用此方法释放的指针的所有权。

```
T* Detach() throw();
```

### <a name="return-value"></a>返回值

返回指针的副本。

### <a name="remarks"></a>备注

释放的指针的所有权，设置[CComPtrBase::p](#p)数据成员变量为 NULL，并返回指针的副本。

##  <a name="isequalobject"></a>  CComPtrBase::IsEqualObject

调用此方法来检查是否指定`IUnknown`指向与关联的相同对象`CComPtrBase`对象。

```
bool IsEqualObject(IUnknown* pOther) throw();
```

### <a name="parameters"></a>参数

*pOther*<br/>
要比较的 `IUnknown *`。

### <a name="return-value"></a>返回值

如果对象为完全相同，则为 false，则返回 true。

##  <a name="operator_not"></a>  CComPtrBase::operator ！

NOT 运算符。

```
bool operator!() const throw();
```

### <a name="return-value"></a>返回值

返回 true 如果`CComHeapPtr`指针为 NULL，等于 false 否则为。

##  <a name="operator_amp"></a>  CComPtrBase::operator &amp;

& 运算符。

```
T** operator&() throw();
```

### <a name="return-value"></a>返回值

返回通过指向的对象的地址`CComPtrBase`对象。

##  <a name="operator_star"></a>  CComPtrBase::operator \*

\* 运算符。

```
T& operator*() const throw();
```

### <a name="return-value"></a>返回值

返回的值[CComPtrBase::p](#p); 即，指向所引用的对象的指针`CComPtrBase`对象。

如果调试版本，如果将出现断言错误[CComPtrBase::p](#p)不等于 NULL。

##  <a name="operator_eq_eq"></a>  CComPtrBase::operator = =

相等运算符。

```
bool operator== (T* pT) const throw();
```

### <a name="parameters"></a>参数

*pT*<br/>
指向对象的指针。

### <a name="return-value"></a>返回值

则返回为 true`CComPtrBase`并*pT*指向同一对象，false 否则。

##  <a name="operator_ptr"></a>  CComPtrBase::operator-&gt;

指针到成员运算符中。

```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```

### <a name="return-value"></a>返回值

返回的值[CComPtrBase::p](#p)数据成员变量。

### <a name="remarks"></a>备注

使用此运算符将指向的类中调用方法`CComPtrBase`对象。 在调试版本中，如果出现断言失败`CComPtrBase`数据成员指向 NULL。

##  <a name="operator_lt"></a>  CComPtrBase::operator &lt;

小于-运算符。

```
bool operator<(T* pT) const throw();
```

### <a name="parameters"></a>参数

*pT*<br/>
指向对象的指针。

### <a name="return-value"></a>返回值

如果由当前对象的指针，则返回 true 小于要比较的指针。

##  <a name="operator_t_star"></a>  CComPtrBase::operator T\*

强制转换运算符。

```
operator T*() const throw();
```

### <a name="remarks"></a>备注

返回一个指向类模板中定义的对象数据类型。

##  <a name="p"></a>  CComPtrBase::p

指针数据成员变量。

```
T* p;
```

### <a name="remarks"></a>备注

此成员变量保存指针信息。

##  <a name="queryinterface"></a>  CComPtrBase::QueryInterface

调用此方法以返回指向指定接口的指针。

```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```

### <a name="parameters"></a>参数

*Q*<br/>
对象需要的类型的接口指针。

*pp*<br/>
接收的请求的接口指针的输出变量的地址。

### <a name="return-value"></a>返回值

返回成功，则 E_NOINTERFACE 失败，则为 S_OK。

### <a name="remarks"></a>备注

此方法调用[iunknown:: Queryinterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))。

在调试版本中，如果出现断言错误*pp*不等于 NULL。

##  <a name="release"></a>  CComPtrBase::Release

调用此方法释放该接口。

```
void Release() throw();
```

### <a name="remarks"></a>备注

释放接口，并[CComPtrBase::p](#p)设置为 NULL。

##  <a name="setsite"></a>  CComPtrBase::SetSite

调用此方法以设置的站点`CComPtrBase`对象传递给`IUnknown`的父对象。

```
HRESULT SetSite(IUnknown* punkParent) throw();
```

### <a name="parameters"></a>参数

*punkParent*<br/>
一个指向`IUnknown`父级的接口。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

此方法调用[AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite)。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
