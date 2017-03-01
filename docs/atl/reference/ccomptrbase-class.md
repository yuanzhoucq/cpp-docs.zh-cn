---
title: "CComPtrBase 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CComPtrBase
- ATL::CComPtrBase<T>
- ATL.CComPtrBase<T>
- ATL::CComPtrBase
- CComPtrBase
dev_langs:
- C++
helpviewer_keywords:
- CComPtrBase class
ms.assetid: 6dbe9543-dee8-4a97-b02f-dd3a25f4a1a0
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 28207e483b0bf56b9e3e98f487d174b8ae47e9e7
ms.lasthandoff: 02/24/2017

---
# <a name="ccomptrbase-class"></a>CComPtrBase 类
此类为使用基于 COM 的内存例程的智能指针类奠定了基础。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>  
class CComPtrBase
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要由智能指针引用的对象类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CComPtrBase:: ~ CComPtrBase](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CComPtrBase::Advise](#advise)|调用此方法以创建之间的连接`CComPtrBase`的连接点和客户端的接收器。|  
|[CComPtrBase::Attach](#attach)|调用此方法以获取现有指针的所有权。|  
|[CComPtrBase::CoCreateInstance](#cocreateinstance)|调用此方法以创建与指定的类 ID 或计划 id。 关联的类的对象|  
|[CComPtrBase::CopyTo](#copyto)|调用此方法以将复制`CComPtrBase`给另一个指针变量的指针。|  
|[CComPtrBase::Detach](#detach)|调用此方法可释放的指针的所有权。|  
|[CComPtrBase::IsEqualObject](#isequalobject)|调用此方法检查是否指定**IUnknown**指向与关联的相同对象`CComPtrBase`对象。|  
|[CComPtrBase::QueryInterface](#queryinterface)|调用此方法以返回指向指定接口的指针。|  
|[CComPtrBase::Release](#release)|调用此方法才能释放接口。|  
|[CComPtrBase::SetSite](#setsite)|调用此方法以将站点设置`CComPtrBase`对象传递给**IUnknown**的父对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CComPtrBase::operator T *](#operator_t_star)|强制转换运算符。|  
|[CComPtrBase::operator ！](#operator_not)|NOT 运算符。|  
|[CComPtrBase::operator.](#operator_amp)|< 运算符。|  
|[CComPtrBase::operator *](#operator_star)|* 运算符。|  
|[CComPtrBase::operator](#ccomptrbase__operator lt)|小于-高于运算符。|  
|[CComPtrBase::operator = =](#operator_eq_eq)|相等运算符。|  
|[-> CComPtrBase::operator](#operator_ptr)|指针到成员运算符中。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CComPtrBase::p](#p)|指针数据成员变量。|  
  
## <a name="remarks"></a>备注  
 此类为其他智能指针，如使用 COM 内存管理例程，该对话框提供了基础[CComQIPtr](../../atl/reference/ccomqiptr-class.md)和[CComPtr](../../atl/reference/ccomptr-class.md)。 派生的类中添加其自己的构造函数和运算符，但依赖于提供的方法`CComPtrBase`。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcomcli.h  
  
##  <a name="a-nameadvisea--ccomptrbaseadvise"></a><a name="advise"></a>CComPtrBase::Advise  
 调用此方法以创建之间的连接`CComPtrBase`的连接点和客户端的接收器。  
  
```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```  
  
### <a name="parameters"></a>参数  
 *pUnk*  
 一个指向客户端的**IUnknown**。  
  
 `iid`  
 连接点的 GUID。 通常情况下，这是管理由连接点的输出接口相同。  
  
 `pdw`  
 Cookie 的唯一标识该连接指向的指针。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 请参阅[AtlAdvise](http://msdn.microsoft.com/library/625a2f03-6b7f-4761-be5d-d2871d1d3254)有关详细信息。  
  
##  <a name="a-nameattacha--ccomptrbaseattach"></a><a name="attach"></a>CComPtrBase::Attach  
 调用此方法以获取现有指针的所有权。  
  
```
void Attach(T* p2) throw();
```  
  
### <a name="parameters"></a>参数  
 `p2`  
 `CComPtrBase`对象将获得 this 指针的所有权。  
  
### <a name="remarks"></a>备注  
 **附加**调用[CComPtrBase::Release](#release)针对现有[CComPtrBase::p](#p)成员变量，然后分配`p2`到`CComPtrBase::p`。 当`CComPtrBase`对象获取的指针的所有权，并将自动调用`Release`情况下对对象的引用计数变为 0，则这将删除指针和任何指针上分配的数据。  
  
##  <a name="a-namedtora--ccomptrbaseccomptrbase"></a><a name="dtor"></a>CComPtrBase:: ~ CComPtrBase  
 析构函数。  
  
```
~CComPtrBase() throw();
```  
  
### <a name="remarks"></a>备注  
 释放由指向接口`CComPtrBase`。  
  
##  <a name="a-namecocreateinstancea--ccomptrbasecocreateinstance"></a><a name="cocreateinstance"></a>CComPtrBase::CoCreateInstance  
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
 `szProgID`  
 指向 ProgID，用来恢复 CLSID 的指针。  
  
 `pUnkOuter`  
 如果**NULL**，指示不创建对象的聚合的一部分。 如果非**NULL**，是指向聚合对象的指针**IUnknown**接口 (控制**IUnknown**)。  
  
 `dwClsContext`  
 管理新创建的对象的代码将在其中运行的上下文。  
  
 `rclsid`  
 与数据和将用于创建对象的代码相关联的 CLSID。  
  
### <a name="return-value"></a>返回值  
 返回成功，或出现 REGDB_E_CLASSNOTREG、 CLASS_E_NOAGGREGATION、 CO_E_CLASSSTRING 或 E_NOINTERFACE 上失败，则为 S_OK。 请参阅[CoCreateClassInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)和[CLSIDFromProgID](http://msdn.microsoft.com/library/windows/desktop/ms688386)有关这些错误的说明。  
  
### <a name="remarks"></a>备注  
 如果调用该方法的第一种形式，则[CLSIDFromProgID](http://msdn.microsoft.com/library/windows/desktop/ms688386)用于恢复的 CLSID。 然后，这两种形式调用[CoCreateClassInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。  
  
 在调试版本中，如果发生断言错误[CComPtrBase::p](#p)是否不等于 NULL。  
  
##  <a name="a-namecopytoa--ccomptrbasecopyto"></a><a name="copyto"></a>CComPtrBase::CopyTo  
 调用此方法以将复制`CComPtrBase`给另一个指针变量的指针。  
  
```
HRESULT CopyTo(T** ppT) throw();
```  
  
### <a name="parameters"></a>参数  
 *ppT*  
 将接收该变量的地址`CComPtrBase`指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，失败了 E_POINTER 会返回 S_OK。  
  
### <a name="remarks"></a>备注  
 副本`CComPtrBase`指针，指向*ppT*。 上的引用计数[CComPtrBase::p](#p)成员变量就会递增。  
  
 如果将返回的 HRESULT 错误*ppT*是否等同于 NULL。 在调试版本中，如果发生断言错误*ppT*是否等同于 NULL。  
  
##  <a name="a-namedetacha--ccomptrbasedetach"></a><a name="detach"></a>CComPtrBase::Detach  
 调用此方法可释放的指针的所有权。  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回指针的副本。  
  
### <a name="remarks"></a>备注  
 释放指针的所有权，设置[CComPtrBase::p](#p)数据成员变量为 NULL，并返回指针的副本。  
  
##  <a name="a-nameisequalobjecta--ccomptrbaseisequalobject"></a><a name="isequalobject"></a>CComPtrBase::IsEqualObject  
 调用此方法检查是否指定**IUnknown**指向与关联的相同对象`CComPtrBase`对象。  
  
```
bool IsEqualObject(IUnknown* pOther) throw();
```  
  
### <a name="parameters"></a>参数  
 `pOther`  
 **IUnknown \* **进行比较。  
  
### <a name="return-value"></a>返回值  
 如果对象均相同，则返回 false，则返回 true。  
  
##  <a name="a-nameoperatornota--ccomptrbaseoperator-"></a><a name="operator_not"></a>CComPtrBase::operator ！  
 NOT 运算符。  
  
```
bool operator!() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回 true 如果`CComHeapPtr`指针是否等同于 NULL、 false 否则为。  
  
##  <a name="a-nameoperatorampa--ccomptrbaseoperator-amp"></a><a name="operator_amp"></a>CComPtrBase::operator&amp;  
 < 运算符。  
  
```
T** operator&() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回指向的对象的地址`CComPtrBase`对象。  
  
##  <a name="a-nameoperatorstara--ccomptrbaseoperator-"></a><a name="operator_star"></a>CComPtrBase::operator *  
 * 运算符。  
  
```
T& operator*() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的值[CComPtrBase::p](#p); 也就是说，指向所引用的对象的指针`CComPtrBase`对象。  
  
 如果调试版本，断言错误将会发生[CComPtrBase::p](#p)是否不等于 NULL。  
  
##  <a name="a-nameoperatoreqeqa--ccomptrbaseoperator-"></a><a name="operator_eq_eq"></a>CComPtrBase::operator = =  
 相等运算符。  
  
```
bool operator== (T* pT) const throw();
```  
  
### <a name="parameters"></a>参数  
 *pT*  
 指向对象的指针。  
  
### <a name="return-value"></a>返回值  
 返回 true if`CComPtrBase`和*pT*指向同一个对象，false 否则。  
  
##  <a name="a-nameoperatorptra--ccomptrbaseoperator--gt"></a><a name="operator_ptr"></a>CComPtrBase::operator-&gt;  

 指针到成员运算符中。  
  
```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的值[CComPtrBase::p](#p)数据成员变量。  
  
### <a name="remarks"></a>备注  
 使用此运算符将指向类中调用的方法`CComPtrBase`对象。 在调试版本中，如果将发生断言失败`CComPtrBase`数据成员将指向 NULL。  
  
##  <a name="a-nameoperatorlta--ccomptrbaseoperator-lt"></a><a name="operator_lt"></a>CComPtrBase::operator&lt;  
 小于-高于运算符。  
  
```
bool operator<(T* pT) const throw();
```  
  
### <a name="parameters"></a>参数  
 *pT*  
 指向对象的指针。  
  
### <a name="return-value"></a>返回值  
 如果当前对象的指针，托管则返回 true 小于要比较的指针。  
  
##  <a name="a-nameoperatortstara--ccomptrbaseoperator-t"></a><a name="operator_t_star"></a>CComPtrBase::operator T *  
 强制转换运算符。  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>备注  
 为类模板中定义的对象数据类型返回的指针。  
  
##  <a name="a-namepa--ccomptrbasep"></a><a name="p"></a>CComPtrBase::p  
 指针数据成员变量。  
  
```
T* p;
```  
  
### <a name="remarks"></a>备注  
 此成员变量包含指针信息。  
  
##  <a name="a-namequeryinterfacea--ccomptrbasequeryinterface"></a><a name="queryinterface"></a>CComPtrBase::QueryInterface  
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
  
 在调试版本中，如果发生断言错误*模式和实施方案*是否不等于 NULL。  
  
##  <a name="a-namereleasea--ccomptrbaserelease"></a><a name="release"></a>CComPtrBase::Release  
 调用此方法才能释放接口。  
  
```
void Release() throw();
```  
  
### <a name="remarks"></a>备注  
 释放该接口，并[CComPtrBase::p](#p)设置为 NULL。  
  
##  <a name="a-namesetsitea--ccomptrbasesetsite"></a><a name="setsite"></a>CComPtrBase::SetSite  
 调用此方法以将站点设置`CComPtrBase`对象传递给**IUnknown**的父对象。  
  
```
HRESULT SetSite(IUnknown* punkParent) throw();
```  
  
### <a name="parameters"></a>参数  
 `punkParent`  
 一个指向**IUnknown**父接口。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 此方法调用[AtlSetChildSite](http://msdn.microsoft.com/library/2a8ece19-6bfd-4e89-9d1d-e5a78f95e2df)。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

