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
ms.openlocfilehash: 740920225fc513a869b4a92344f87004831e4768
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864943"
---
# <a name="ccomptrbase-class"></a>CComPtrBase 类

此类为使用基于 COM 的内存例程的智能指针类提供基础。

## <a name="syntax"></a>语法

```
template <class T>
class CComPtrBase
```

#### <a name="parameters"></a>parameters

*T*<br/>
智能指针所引用的对象类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComPtrBase：： ~ CComPtrBase](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComPtrBase：： Advise](#advise)|调用此方法可在 `CComPtrBase`的连接点和客户端接收器之间创建连接。|
|[CComPtrBase：： Attach](#attach)|调用此方法以获取现有指针的所有权。|
|[CComPtrBase：： CoCreateInstance](#cocreateinstance)|调用此方法以创建与指定类 ID 或程序 ID 相关联的类的对象。|
|[CComPtrBase：： CopyTo](#copyto)|调用此方法可将 `CComPtrBase` 指针复制到另一个指针变量。|
|[CComPtrBase：:D etach](#detach)|调用此方法可释放指针的所有权。|
|[CComPtrBase::IsEqualObject](#isequalobject)|调用此方法以检查指定的 `IUnknown` 是否指向与 `CComPtrBase` 对象关联的同一对象。|
|[CComPtrBase：： QueryInterface](#queryinterface)|调用此方法以返回指向指定接口的指针。|
|[CComPtrBase：： Release](#release)|调用此方法可释放接口。|
|[CComPtrBase：： SetSite](#setsite)|调用此方法可将 `CComPtrBase` 对象的站点设置为父对象的 `IUnknown`。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CComPtrBase：： operator T *](#operator_t_star)|转换运算符。|
|[CComPtrBase：： operator！](#operator_not)|NOT 运算符。|
|[CComPtrBase：： operator &](#operator_amp)|& 运算符。|
|[CComPtrBase：： operator *](#operator_star)|\* 运算符。|
|[CComPtrBase：： operator <](#ccomptrbase__operator lt)|小于运算符。|
|[CComPtrBase：： operator = =](#operator_eq_eq)|相等运算符。|
|[CComPtrBase：： operator->](#operator_ptr)|指向成员的指针运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CComPtrBase：:p](#p)|指针数据成员变量。|

## <a name="remarks"></a>备注

此类为使用 COM 内存管理例程的其他智能指针（例如[CComQIPtr](../../atl/reference/ccomqiptr-class.md)和[CComPtr](../../atl/reference/ccomptr-class.md)）提供基础。 派生类添加自己的构造函数和运算符，但依赖于 `CComPtrBase`提供的方法。

## <a name="requirements"></a>要求

**标头：** atlcomcli。h

##  <a name="advise"></a>CComPtrBase：： Advise

调用此方法可在 `CComPtrBase`的连接点和客户端接收器之间创建连接。

```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```

### <a name="parameters"></a>parameters

*pUnk*<br/>
指向客户端的 `IUnknown`的指针。

*iid*<br/>
连接点的 GUID。 通常，这与连接点管理的输出接口相同。

*pdw*<br/>
一个指针，指向用于唯一标识连接的 cookie。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

有关详细信息，请参阅[AtlAdvise](connection-point-global-functions.md#atladvise) 。

##  <a name="attach"></a>CComPtrBase：： Attach

调用此方法以获取现有指针的所有权。

```
void Attach(T* p2) throw();
```

### <a name="parameters"></a>parameters

*p2*<br/>
`CComPtrBase` 对象将取得此指针的所有权。

### <a name="remarks"></a>备注

`Attach` 在现有的[CComPtrBase：:p](#p)成员变量上调用[CComPtrBase：： Release](#release) ，然后将*p2*分配给 `CComPtrBase::p`。 当 `CComPtrBase` 对象取得指针的所有权时，它会自动调用指针上的 `Release`，如果对象的引用计数为0，则将删除该指针和任何分配的数据。

##  <a name="dtor"></a>CComPtrBase：： ~ CComPtrBase

析构函数。

```
~CComPtrBase() throw();
```

### <a name="remarks"></a>备注

释放 `CComPtrBase`指向的接口。

##  <a name="cocreateinstance"></a>CComPtrBase：： CoCreateInstance

调用此方法以创建与指定类 ID 或程序 ID 相关联的类的对象。

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

### <a name="parameters"></a>parameters

*szProgID*<br/>
一个指针，指向用于恢复 CLSID 的 ProgID。

*pUnkOuter*<br/>
如果为 NULL，则指示对象未作为聚合的一部分创建。 如果非 NULL，则为指向聚合对象的 `IUnknown` 接口的指针（控制 `IUnknown`）。

*dwClsContext*<br/>
用于管理新创建的对象的代码将运行的上下文。

*rclsid*<br/>
与将用于创建对象的数据和代码关联的 CLSID。

### <a name="return-value"></a>返回值

返回 S_OK 成功，或者 REGDB_E_CLASSNOTREG、CLASS_E_NOAGGREGATION、CO_E_CLASSSTRING 或 E_NOINTERFACE 失败。 有关这些错误的说明，请参阅[CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)和[CLSIDFromProgID](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid) 。

### <a name="remarks"></a>备注

如果调用方法的第一种形式，将使用[CLSIDFromProgID](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid)来恢复 CLSID。 然后，两个窗体调用[CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)。

在调试版本中，如果[CComPtrBase：:p](#p)不等于 NULL，则将发生断言错误。

##  <a name="copyto"></a>CComPtrBase：： CopyTo

调用此方法可将 `CComPtrBase` 指针复制到另一个指针变量。

```
HRESULT CopyTo(T** ppT) throw();
```

### <a name="parameters"></a>parameters

*ppT*<br/>
将接收 `CComPtrBase` 指针的变量的地址。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK，E_POINTER 失败。

### <a name="remarks"></a>备注

将 `CComPtrBase` 指针复制到*ppT*。 [CComPtrBase：:p](#p)成员变量的引用计数将递增。

如果*ppT*等于 NULL，则将返回错误 HRESULT。 在调试版本中，如果*ppT*等于 NULL，则将发生断言错误。

##  <a name="detach"></a>CComPtrBase：:D etach

调用此方法可释放指针的所有权。

```
T* Detach() throw();
```

### <a name="return-value"></a>返回值

返回指针的副本。

### <a name="remarks"></a>备注

释放指针的所有权，将[CComPtrBase：:p](#p)数据成员变量设置为 NULL，并返回指针的副本。

##  <a name="isequalobject"></a>CComPtrBase::IsEqualObject

调用此方法以检查指定的 `IUnknown` 是否指向与 `CComPtrBase` 对象关联的同一对象。

```
bool IsEqualObject(IUnknown* pOther) throw();
```

### <a name="parameters"></a>parameters

*pOther*<br/>
要比较的 `IUnknown *`。

### <a name="return-value"></a>返回值

如果对象相同，则返回 true，否则返回 false。

##  <a name="operator_not"></a>CComPtrBase：： operator！

NOT 运算符。

```
bool operator!() const throw();
```

### <a name="return-value"></a>返回值

如果 `CComHeapPtr` 指针等于 NULL，则返回 true，否则返回 false。

##  <a name="operator_amp"></a>CComPtrBase：： operator &amp;

& 运算符。

```
T** operator&() throw();
```

### <a name="return-value"></a>返回值

返回 `CComPtrBase` 对象所指向的对象的地址。

##  <a name="operator_star"></a>CComPtrBase：： operator \*

\* 运算符。

```
T& operator*() const throw();
```

### <a name="return-value"></a>返回值

返回 CComPtrBase 的值[：:p](#p);也就是说，指向 `CComPtrBase` 对象所引用的对象的指针。

如果为调试生成，则在[CComPtrBase：:p](#p)不等于 NULL 时，将发生断言错误。

##  <a name="operator_eq_eq"></a>CComPtrBase：： operator = =

相等运算符。

```
bool operator== (T* pT) const throw();
```

### <a name="parameters"></a>parameters

*五*<br/>
指向对象的指针。

### <a name="return-value"></a>返回值

如果 `CComPtrBase` 和*pT*指向同一个对象，则返回 true，否则返回 false。

##  <a name="operator_ptr"></a>CComPtrBase：： operator-&gt;

指向成员的指针运算符。

```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```

### <a name="return-value"></a>返回值

返回[CComPtrBase：:p](#p)数据成员变量的值。

### <a name="remarks"></a>备注

使用此运算符可调用 `CComPtrBase` 对象所指向的类中的方法。 在调试版本中，如果 `CComPtrBase` 数据成员指向 NULL，则将发生断言失败。

##  <a name="operator_lt"></a>CComPtrBase：： operator &lt;

小于运算符。

```
bool operator<(T* pT) const throw();
```

### <a name="parameters"></a>parameters

*五*<br/>
指向对象的指针。

### <a name="return-value"></a>返回值

如果当前对象管理的指针小于要比较的指针，则返回 true。

##  <a name="operator_t_star"></a>CComPtrBase：： operator T\*

转换运算符。

```
operator T*() const throw();
```

### <a name="remarks"></a>备注

返回一个指针，该指针指向在类模板中定义的对象数据类型。

##  <a name="p"></a>CComPtrBase：:p

指针数据成员变量。

```
T* p;
```

### <a name="remarks"></a>备注

此成员变量保存指针信息。

##  <a name="queryinterface"></a>CComPtrBase：： QueryInterface

调用此方法以返回指向指定接口的指针。

```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```

### <a name="parameters"></a>parameters

*Q*<br/>
需要其接口指针的对象类型。

*pp*<br/>
输出变量的地址，该变量接收请求的接口指针。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回 E_NOINTERFACE。

### <a name="remarks"></a>备注

此方法调用[IUnknown：： QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))。

在调试版本中，如果*pp*不等于 NULL，则将发生断言错误。

##  <a name="release"></a>CComPtrBase：： Release

调用此方法可释放接口。

```
void Release() throw();
```

### <a name="remarks"></a>备注

接口已释放， [CComPtrBase：:p](#p)设置为 NULL。

##  <a name="setsite"></a>CComPtrBase：： SetSite

调用此方法可将 `CComPtrBase` 对象的站点设置为父对象的 `IUnknown`。

```
HRESULT SetSite(IUnknown* punkParent) throw();
```

### <a name="parameters"></a>parameters

*punkParent*<br/>
指向父级的 `IUnknown` 接口的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

此方法调用[AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite)。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
