---
title: "CComClassFactorySingleton 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton::CreateInstance
- ATLCOM/ATL::CComClassFactorySingleton::m_spObj
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 165bc85a0b00ac8186e5a145a75c4478335b5e0e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ccomclassfactorysingleton-class"></a>CComClassFactorySingleton 类
此类派生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)并使用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)构造单个对象。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>  
class CComClassFactorySingleton : public CComClassFactory
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类。  
  
 `CComClassFactorySingleton`派生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)并使用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)构造单个对象。 每次调用`CreateInstance`方法只需查询此对象的接口指针。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComClassFactorySingleton::CreateInstance](#createinstance)|查询`m_spObj`的接口指针。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CComClassFactorySingleton::m_spObj](#m_spobj)|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)对象通过构造`CComClassFactorySingleton`。|  
  
## <a name="remarks"></a>备注  
 ATL 对象通常通过派生自获取类工厂[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 此类包括宏[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)，其中声明`CComClassFactory`作为默认类工厂。 若要使用`CComClassFactorySingleton`，指定[DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton)对象的类定义中的宏。 例如:  
  
 [!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory`  
  
 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)  
  
 `CComClassFactorySingleton`  
  
## <a name="requirements"></a>惠?  
 **标头：** atlcom.h  
  
##  <a name="createinstance"></a>CComClassFactorySingleton::CreateInstance  
 调用`QueryInterface`通过[m_spObj](#m_spobj)检索的接口指针。  
  
```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```  
  
### <a name="parameters"></a>参数  
 `pUnkOuter`  
 [in]如果该对象正在创建的聚合时，一部分然后`pUnkOuter`必须是未知的外部对象。 否则为`pUnkOuter`必须**NULL**。  
  
 `riid`  
 [in]所请求的接口的 IID。 如果`pUnkOuter`为非**NULL**，`riid`必须**IID_IUnknown**。  
  
 `ppvObj`  
 [out]指向由标识的接口指针的指针`riid`。 如果对象不支持此接口，`ppvObj`设置为**NULL**。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="m_spobj"></a>CComClassFactorySingleton::m_spObj  
 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)对象通过构造`CComClassFactorySingleton`。  
  
```
CComPtr<IUnknown> m_spObj;
```  
  
### <a name="remarks"></a>备注  
 每次调用[CreateInstance](#createinstance)方法只需查询此对象的接口指针。  
  
 请注意，当前窗体的`m_spObj`提供一项重大更改的方式，`CComClassFactorySingleton`处理在以前版本的 atl。 在早期版本中`CComClassFactorySingleton`作为类工厂，同时在服务器初始化过程中创建对象。 在 Visual c + +.NET 2003 中，该对象创建延迟，在首次请求。 此更改可能会导致程序依赖于早期初始化错误。  
  
## <a name="see-also"></a>请参阅  
 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)   
 [CComClassFactory2 类](../../atl/reference/ccomclassfactory2-class.md)   
 [CComClassFactoryAutoThread 类](../../atl/reference/ccomclassfactoryautothread-class.md)   
 [CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [类概述](../../atl/atl-class-overview.md)
