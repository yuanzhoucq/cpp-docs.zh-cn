---
title: "CComObject 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComObject
- ATLCOM/ATL::CComObject
- ATLCOM/ATL::CComObject::CComObject
- ATLCOM/ATL::CComObject::AddRef
- ATLCOM/ATL::CComObject::CreateInstance
- ATLCOM/ATL::CComObject::QueryInterface
- ATLCOM/ATL::CComObject::Release
dev_langs:
- C++
helpviewer_keywords:
- CComObject class
ms.assetid: e2b6433b-6349-4749-b4bc-acbd7a22c8b0
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 5f752b96d4a722fbddfcc9e5be3a82b8b12a86a1
ms.lasthandoff: 02/24/2017

---
# <a name="ccomobject-class"></a>CComObject 类
此类实现**IUnknown**非聚合对象。  
  
## <a name="syntax"></a>语法  
  
```
template<class Base>  
class CComObject : public Base
```  
  
#### <a name="parameters"></a>参数  
 `Base`  
 您的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如你想要在对象上支持任何其他接口也一样。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CComObject::CComObject](#ccomobject)|构造函数。|  
|[CComObject:: ~ CComObject](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CComObject::AddRef](#addref)|递增对对象的引用计数。|  
|[CComObject::CreateInstance](#createinstance)|（静态）创建一个新`CComObject`对象。|  
|[CComObject::QueryInterface](#queryinterface)|检索指向所请求的接口的指针。|  
|[CComObject::Release](#release)|递减引用计数对象。|  
  
## <a name="remarks"></a>备注  
 `CComObject`实现[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)非聚合对象。 但是，调用`QueryInterface`， `AddRef`，和**版本**委派给`CComObjectRootEx`。  
  
 有关使用`CComObject`，请参阅文章[ATL COM 对象的基础知识](../../atl/fundamentals-of-atl-com-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `Base`  
  
 `CComObject`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="addref"></a>CComObject::AddRef  
 递增对对象的引用计数。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>返回值  
 此函数返回的对象的新递增的引用计数。 此值可用于诊断或测试。  
  
##  <a name="ccomobject"></a>CComObject::CComObject  
 构造函数会增加模块锁计数。  
  
```
CComObject(void* = NULL);
```  
  
### <a name="parameters"></a>参数  
 **void\***  
 [in]未使用此未命名的参数。 它位于与其他对称**CCom***XXX*`Object`*XXX*构造函数。  
  
### <a name="remarks"></a>备注  
 析构函数递减它。  
  
 如果`CComObject`-成功使用构造派生的对象**新**运算符，在初始引用计数为 0。 若要设置为适当的值 (1) 的引用计数，请调用[AddRef](#addref)函数。  
  
##  <a name="dtor"></a>CComObject:: ~ CComObject  
 析构函数。  
  
```
CComObject();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源，调用[FinalRelease](ccomobjectrootex-class.md#finalrelease)，并减少模块锁计数。  

  
##  <a name="createinstance"></a>CComObject::CreateInstance  
 此静态函数允许您创建一个新**CComObject** `Base` ** > **对象，而不需要的开销[CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。  
  
```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```  
  
### <a name="parameters"></a>参数  
 `pp`  
 [out]一个指向**CComObject** `Base` ** > **指针。 如果`CreateInstance`不成功，`pp`设置为**NULL**。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 返回的对象具有引用计数为零，因此请调用`AddRef`立即，然后使用**版本**以完成后释放对对象指针的引用。  
  
 如果执行不需要直接访问对象，但仍想要创建新的对象，而不需要的开销`CoCreateInstance`，使用[CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance)相反。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM&#38;](../../atl/codesnippet/cpp/ccomobject-class_1.h)]  
  
 [!code-cpp[NVC_ATL_COM&#39;](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]  
  
##  <a name="queryinterface"></a>CComObject::QueryInterface  
 检索指向所请求的接口的指针。  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>  
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]正在请求的接口的标识符。  
  
 `ppvObject`  
 [out]指向由标识的接口指针的指针`iid`。 如果该对象不支持此接口，`ppvObject`设置为**NULL**。  
  
 `pp`  
 [out]指向由类型标识的接口指针的指针`Q`。 如果该对象不支持此接口，`pp`设置为**NULL**。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="release"></a>CComObject::Release  
 递减引用计数对象。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>返回值  
 此函数返回的对象的新递减引用计数。 在调试版本中，则返回值可能有用的诊断或测试。 在非调试生成中，**版本**始终返回 0。  
  
## <a name="see-also"></a>另请参阅  
 [CComAggObject 类](../../atl/reference/ccomaggobject-class.md)   
 [CComPolyObject 类](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE_AGGREGATABLE](http://msdn.microsoft.com/library/e7e568d7-04e0-4226-b5dc-224deed229ab)   
 [DECLARE_NOT_AGGREGATABLE](http://msdn.microsoft.com/library/2a116c7c-bab8-4f2a-a9ad-03d7aba0f762)   
 [类概述](../../atl/atl-class-overview.md)

