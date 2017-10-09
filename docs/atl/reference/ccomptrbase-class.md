---
title: "CComPtrBase 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CComPtrBase class
ms.assetid: 6dbe9543-dee8-4a97-b02f-dd3a25f4a1a0
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: c55726a1728185f699afbac4ba68a6dc0f70c2bf
ms.openlocfilehash: 1e6bf79ce5de5d19468b3cbb230e16882483dc30
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="ccomptrbase-class"></a>CComPtrBase 类
此类为使用基于 COM 的内存例程的智能指针类提供基础。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>  
class CComPtrBase
```  
  
#### <a name="parameters"></a>参数  
 `T`  
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
|[CComPtrBase::Attach](#attach)|调用此方法需要现有指针的所有权。|  
|[CComPtrBase::CoCreateInstance](#cocreateinstance)|调用此方法以创建与指定的类 ID 或程序 id。 关联的类的对象|  
|[CComPtrBase::CopyTo](#copyto)|调用此方法以将复制`CComPtrBase`给另一个指针变量的指针。|  
|[CComPtrBase::Detach](#detach)|调用此方法可释放的指针的所有权。|  
|[CComPtrBase::IsEqualObject](#isequalobject)|调用此方法用于检查是否指定**IUnknown**指向与关联的相同对象`CComPtrBase`对象。|  
|[CComPtrBase::QueryInterface](#queryinterface)|调用此方法以返回指向指定接口的指针。|  
|[CComPtrBase::Release](#release)|调用此方法来释放接口。|  
|[CComPtrBase::SetSite](#setsite)|调用此方法以设置的站点`CComPtrBase`对象传递给**IUnknown**的父对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CComPtrBase::operator T *](#operator_t_star)|强制转换运算符。|  
|[CComPtrBase::operator ！](#operator_not)|NOT 运算符。|  
|[CComPtrBase::operator （& a)](#operator_amp)|& 运算符。|  
|[CComPtrBase::operator *](#operator_star)|* 运算符。|  
|[CComPtrBase::operator <](#ccomptrbase__operator lt)|小于-高于运算符。|  
|[CComPtrBase::operator = =](#operator_eq_eq)|相等运算符。|  
|[CComPtrBase::operator->](#operator_ptr)|指针到成员运算符中。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CComPtrBase::p](#p)|指针数据成员变量。|  
  
## <a name="remarks"></a>备注  
 此类为其他智能指针，如使用 COM 内存管理例程，该对话框提供了基础[CComQIPtr](../../atl/reference/ccomqiptr-class.md)和[CComPtr](../../atl/reference/ccomptr-class.md)。 派生的类中添加自己的构造函数和运算符，但是在提供的方法依赖于`CComPtrBase`。  
  
## <a name="requirements"></a>要求  
 **标头：** atlcomcli.h  
  
##  <a name="advise"></a>CComPtrBase::Advise  
 调用此方法以之间创建连接`CComPtrBase`的连接点和客户端的接收器。  
  
```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```  
  
### <a name="parameters"></a>参数  
 *pUnk*  
 指向客户端的**IUnknown**。  
  
 `iid`  
 连接点的 GUID。 通常，这是由连接点的传出接口相同。  
  
 `pdw`  
 指向，唯一标识连接的 cookie 的指针。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 请参阅[AtlAdvise](connection-point-global-functions.md#atladvise)有关详细信息。  
  
##  <a name="attach"></a>CComPtrBase::Attach  
 调用此方法需要现有指针的所有权。  
  
```
void Attach(T* p2) throw();
```  
  
### <a name="parameters"></a>参数  
 `p2`  
 `CComPtrBase`对象将获得 this 指针的所有权。  
  
### <a name="remarks"></a>备注  
 **附加**调用[CComPtrBase::Release](#release)上现有[CComPtrBase::p](#p)成员变量，然后将分配`p2`到`CComPtrBase::p`。 当`CComPtrBase`对象采用的指针的所有权，它将自动调用`Release`如果上对象的引用计数变为 0，则这将删除指针和任何指针上分配数据。  
  
##  <a name="dtor"></a>CComPtrBase:: ~ CComPtrBase  
 析构函数。  
  
```
~CComPtrBase() throw();
```  
  
### <a name="remarks"></a>备注  
 释放由指向接口`CComPtrBase`。  
  
##  <a name="cocreateinstance"></a>CComPtrBase::CoCreateInstance  
 调用此方法以创建与指定的类 ID 或程序 id。 关联的类的对象  
  
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
 `szProgID`  
 指向 ProgID，用来恢复 CLSID 的指针。  
  
 `pUnkOuter`  
 如果**NULL**，指示不创建对象聚合的一部分。 如果非**NULL**，是指向聚合对象的指针**IUnknown**接口 (控制**IUnknown**)。  
  
 `dwClsContext`  
 管理新创建的对象的代码将在其中运行的上下文。  
  
 `rclsid`  
 与关联的数据以及将用于创建对象的代码的 CLSID。  
  
### <a name="return-value"></a>返回值  
 返回成功，或 REGDB_E_CLASSNOTREG、 CLASS_E_NOAGGREGATION、 CO_E_CLASSSTRING 或 E_NOINTERFACE 上失败，则为 S_OK。 请参阅[CoCreateClassInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)和[CLSIDFromProgID](http://msdn.microsoft.com/library/windows/desktop/ms688386)有关这些错误的说明。  
  
### <a name="remarks"></a>备注  
 如果调用该方法的第一种形式，则[CLSIDFromProgID](http://msdn.microsoft.com/library/windows/desktop/ms688386)用于恢复的 CLSID。 然后调用这两种形式[CoCreateClassInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。  
  
 在调试版本中，如果出现断言错误[CComPtrBase::p](#p)是否不等于 NULL。  
  
##  <a name="copyto"></a>CComPtrBase::CopyTo  
 调用此方法以将复制`CComPtrBase`给另一个指针变量的指针。  
  
```
HRESULT CopyTo(T** ppT) throw();
```  
  
### <a name="parameters"></a>参数  
 *ppT*  
 将接收变量的地址`CComPtrBase`指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，失败的 E_POINTER 返回，则为 S_OK。  
  
### <a name="remarks"></a>备注  
 副本`CComPtrBase`指向*ppT*。 上的引用计数[CComPtrBase::p](#p)成员变量将递增。  
  
 如果将返回 HRESULT 的错误*ppT*等于为 NULL。 在调试版本中，如果出现断言错误*ppT*等于为 NULL。  
  
##  <a name="detach"></a>CComPtrBase::Detach  
 调用此方法可释放的指针的所有权。  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回指针的副本。  
  
### <a name="remarks"></a>备注  
 释放的指针的所有权，设置[CComPtrBase::p](#p)数据成员变量为 NULL，并返回指针的副本。  
  
##  <a name="isequalobject"></a>CComPtrBase::IsEqualObject  
 调用此方法用于检查是否指定**IUnknown**指向与关联的相同对象`CComPtrBase`对象。  
  
```
bool IsEqualObject(IUnknown* pOther) throw();
```  
  
### <a name="parameters"></a>参数  
 `pOther`  
 **IUnknown \*** 进行比较。  
  
### <a name="return-value"></a>返回值  
 如果对象均相同，则返回 false，则返回 true。  
  
##  <a name="operator_not"></a>CComPtrBase::operator ！  
 NOT 运算符。  
  
```
bool operator!() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回 true 如果`CComHeapPtr`指针为 NULL，等于 false 否则为。  
  
##  <a name="operator_amp"></a>CComPtrBase::operator&amp;  
 & 运算符。  
  
```
T** operator&() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回指向对象的地址`CComPtrBase`对象。  
  
##  <a name="operator_star"></a>CComPtrBase::operator *  
 * 运算符。  
  
```
T& operator*() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的值[CComPtrBase::p](#p); 即，指向所引用的对象的指针`CComPtrBase`对象。  
  
 如果调试版本，如果将出现断言错误[CComPtrBase::p](#p)是否不等于 NULL。  
  
##  <a name="operator_eq_eq"></a>CComPtrBase::operator = =  
 相等运算符。  
  
```
bool operator== (T* pT) const throw();
```  
  
### <a name="parameters"></a>参数  
 *pT*  
 指向对象的指针。  
  
### <a name="return-value"></a>返回值  
 返回 true 如果`CComPtrBase`和*pT*指向同一对象，false 否则。  
  
##  <a name="operator_ptr"></a>CComPtrBase::operator-&gt;  

 指针到成员运算符中。  
  
```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的值[CComPtrBase::p](#p)数据成员变量。  
  
### <a name="remarks"></a>备注  
 使用此运算符的指向类中调用的方法`CComPtrBase`对象。 调试版本中，如果断言失败会发生`CComPtrBase`数据成员点为 NULL。  
  
##  <a name="operator_lt"></a>CComPtrBase::operator&lt;  
 小于-高于运算符。  
  
```
bool operator<(T* pT) const throw();
```  
  
### <a name="parameters"></a>参数  
 *pT*  
 指向对象的指针。  
  
### <a name="return-value"></a>返回值  
 如果由当前对象的指针，则返回 true 小于要比较的指针。  
  
##  <a name="operator_t_star"></a>CComPtrBase::operator T *  
 强制转换运算符。  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>备注  
 将指针返回到类模板中定义的对象数据类型。  
  
##  <a name="p"></a>CComPtrBase::p  
 指针数据成员变量。  
  
```
T* p;
```  
  
### <a name="remarks"></a>备注  
 此成员变量包含的指针信息。  
  
##  <a name="queryinterface"></a>CComPtrBase::QueryInterface  
 调用此方法以返回指向指定接口的指针。  
  
```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```  
  
### <a name="parameters"></a>参数  
 `Q`  
 对象类型的接口指针是必需的。  
  
 `pp`  
 接收的请求的接口指针的输出变量的地址。  
  
### <a name="return-value"></a>返回值  
 返回成功，则 E_NOINTERFACE 失败，则为 S_OK。  
  
### <a name="remarks"></a>备注  
 此方法调用[iunknown:: Queryinterface](http://msdn.microsoft.com/library/windows/desktop/ms682521)。  
  
 在调试版本中，如果出现断言错误*pp*是否不等于 NULL。  
  
##  <a name="release"></a>CComPtrBase::Release  
 调用此方法来释放接口。  
  
```
void Release() throw();
```  
  
### <a name="remarks"></a>备注  
 接口被释放，和[CComPtrBase::p](#p)设置为 NULL。  
  
##  <a name="setsite"></a>CComPtrBase::SetSite  
 调用此方法以设置的站点`CComPtrBase`对象传递给**IUnknown**的父对象。  
  
```
HRESULT SetSite(IUnknown* punkParent) throw();
```  
  
### <a name="parameters"></a>参数  
 `punkParent`  
 指向的指针**IUnknown**的父级的接口。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 此方法调用[AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite)。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

