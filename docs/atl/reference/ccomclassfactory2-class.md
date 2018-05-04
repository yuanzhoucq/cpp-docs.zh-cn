---
title: CComClassFactory2 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComClassFactory2
- ATLCOM/ATL::CComClassFactory2
- ATLCOM/ATL::CComClassFactory2::CreateInstance
- ATLCOM/ATL::CComClassFactory2::CreateInstanceLic
- ATLCOM/ATL::CComClassFactory2::GetLicInfo
- ATLCOM/ATL::CComClassFactory2::LockServer
- ATLCOM/ATL::CComClassFactory2::RequestLicKey
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactory2 class
ms.assetid: 19b66fd6-b9ed-47a0-822c-8132184f5a3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: da2b47290d3d0be525ca65b16733c9f42835d24e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="ccomclassfactory2-class"></a>CComClassFactory2 类
此类实现[IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720)接口。  
  
## <a name="syntax"></a>语法  
  
```
template <class license>  
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```  
  
#### <a name="parameters"></a>参数  
 *许可证*  
 实现以下静态函数的类：  
  
- **静态 BOOL VerifyLicenseKey (BSTR** `bstr` **);**  
  
- **静态 BOOL GetLicenseKey (DWORD** `dwReserved` **，BSTR\***  `pBstr` **);**  
  
- **静态 BOOL IsLicenseValid （);**  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComClassFactory2::CreateInstance](#createinstance)|创建指定的 CLSID 的对象。|  
|[CComClassFactory2::CreateInstanceLic](#createinstancelic)|给定的许可密钥，创建指定的 CLSID 的对象。|  
|[CComClassFactory2::GetLicInfo](#getlicinfo)|检索描述类工厂的授权功能的信息。|  
|[CComClassFactory2::LockServer](#lockserver)|锁定内存中的类工厂。|  
|[CComClassFactory2::RequestLicKey](#requestlickey)|创建并返回的许可密钥。|  
  
## <a name="remarks"></a>备注  
 `CComClassFactory2` 实现[IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720)接口，该扩展的[IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)。 **IClassFactory2**控件对象通过许可证的创建。 类工厂执行许可的计算机上可以提供运行时许可证密钥。 此许可证密钥允许应用程序在完整的计算机许可证不存在时实例化对象。  
  
 ATL 对象通常通过派生自获取类工厂[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 此类包括宏[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)，其中声明[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)作为默认类工厂。 若要使用`CComClassFactory2`，指定[DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)对象的类定义中的宏。 例如：  
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]  
  
 **CMyLicense**的模板参数`CComClassFactory2`，必须实现的静态函数`VerifyLicenseKey`， `GetLicenseKey`，和`IsLicenseValid`。 下面是简单许可证类的一个示例：  
  
 [!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]  
  
 `CComClassFactory2` 从这两个派生**CComClassFactory2Base**和*许可证*。 **CComClassFactory2Base**，反过来，派生自**IClassFactory2**和**CComObjectRootEx\< CComGlobalsThreadModel >**。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CComObjectRootBase`  
  
 `license`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory2`  
  
 `CComClassFactory2`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcom.h  
  
##  <a name="createinstance"></a>  CComClassFactory2::CreateInstance  
 创建指定的 CLSID 的对象并检索到此对象的接口指针。  
  
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
  
### <a name="remarks"></a>备注  
 要求计算机完全获得许可。 如果完整的计算机许可证不存在，则调用[CreateInstanceLic](#createinstancelic)。  
  
##  <a name="createinstancelic"></a>  CComClassFactory2::CreateInstanceLic  
 类似于[CreateInstance](#createinstance)，只不过`CreateInstanceLic`需要许可证密钥。  
  
```
STDMETHOD(CreateInstanceLic)(
    IUnknown* pUnkOuter,
    IUnknown* /* pUnkReserved
 */,
    REFIID riid,
    BSTR bstrKey,
    void** ppvObject);
```  
  
### <a name="parameters"></a>参数  
 `pUnkOuter`  
 [in]如果该对象正在创建的聚合时，一部分然后`pUnkOuter`必须是未知的外部对象。 否则为`pUnkOuter`必须**NULL**。  
  
 *pUnkReserved*  
 [in]未使用。 必须是**NULL**。  
  
 `riid`  
 [in]所请求的接口的 IID。 如果`pUnkOuter`为非**NULL**，`riid`必须**IID_IUnknown**。  
  
 `bstrKey`  
 [in]运行时许可证密钥以前通过调用中获取`RequestLicKey`。 创建该对象需要此密钥。  
  
 `ppvObject`  
 [out]指向由指定的接口指针的指针`riid`。 如果对象不支持此接口，`ppvObject`设置为**NULL**。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 你可以获取许可证密钥 using [RequestLicKey](#requestlickey)。 若要在未授权的计算机上创建一个对象，您必须调用`CreateInstanceLic`。  
  
##  <a name="getlicinfo"></a>  CComClassFactory2::GetLicInfo  
 填充[LICINFO](http://msdn.microsoft.com/library/windows/desktop/ms690590)描述类工厂的信息的结构的授权功能。  
  
```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```  
  
### <a name="parameters"></a>参数  
 *pLicInfo*  
 [out]指向**LICINFO**结构。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 `fRuntimeKeyAvail`此结构的成员该值指示是否，给定的许可密钥，类工厂允许在未授权的计算机上创建的对象。 *FLicVerified*成员指示完整的计算机许可证是否存在。  
  
##  <a name="lockserver"></a>  CComClassFactory2::LockServer  
 递增和递减模块锁计数通过调用 **_Module::Lock**和 **_Module::Unlock**分别。  
  
```
STDMETHOD(LockServer)(BOOL fLock);
```  
  
### <a name="parameters"></a>参数  
 `fLock`  
 [in]如果**TRUE**、 的锁计数递增; 否则为的锁计数会递减。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 **_Module**的全局实例是指[CComModule](../../atl/reference/ccommodule-class.md)或从它派生的类。  
  
 调用`LockServer`允许客户端，以便可以快速创建多个对象保留的类工厂。  
  
##  <a name="requestlickey"></a>  CComClassFactory2::RequestLicKey  
 创建并返回许可证密钥，前提`fRuntimeKeyAvail`的成员[LICINFO](http://msdn.microsoft.com/library/windows/desktop/ms690590)结构是**TRUE**。  
  
```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```  
  
### <a name="parameters"></a>参数  
 `dwReserved`  
 [in]未使用。 必须为零。  
  
 `pbstrKey`  
 [out]指向指针的许可证密钥。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 加密时需要调用许可证密钥[CreateInstanceLic](#createinstancelic)以未授权的计算机上创建对象。 如果`fRuntimeKeyAvail`是**FALSE**，则仅可以在完全授权的计算机上创建对象。  
  
 调用[GetLicInfo](#getlicinfo)若要检索的值`fRuntimeKeyAvail`。  
  
## <a name="see-also"></a>请参阅  
 [CComClassFactoryAutoThread 类](../../atl/reference/ccomclassfactoryautothread-class.md)   
 [CComClassFactorySingleton 类](../../atl/reference/ccomclassfactorysingleton-class.md)   
 [CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [类概述](../../atl/atl-class-overview.md)
