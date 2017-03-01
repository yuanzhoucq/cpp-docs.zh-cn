---
title: "服务器注册的全局函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 4ace3bb50d824827071260e3f43cec3cda32742f
ms.lasthandoff: 02/24/2017

---
# <a name="server-registration-global-functions"></a>服务器注册的全局函数
这些函数提供支持用于注册和注销在对象映射中的服务器对象。  
  
> [!IMPORTANT]
>  下表中列出的函数不能用于应用程序中执行[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
|||  
|-|-|  
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|调用此函数可在对象映射中注册所有对象。|  
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|调用此函数可在对象映射中注销所有对象。|  
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|调用此函数可注册类对象。|  
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|若要撤消 COM 模块中的类对象，调用此函数。|  
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|调用此函数可获取的类对象。|  

## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
   
##  <a name="a-nameatlcommoduleregisterservera--atlcommoduleregisterserver"></a><a name="atlcommoduleregisterserver"></a>AtlComModuleRegisterServer  
 调用此函数可在对象映射中注册所有对象。  
  
```
ATLINLINE ATLAPI AtlComModuleRegisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bRegTypeLib,
    const CLSID* pCLSID);
```  
  
### <a name="parameters"></a>参数  
 `pComModule`  
 对 COM 模块的指针。  
  
 `bRegTypeLib`  
 如果要注册类型库，则为 TRUE。  
  
 `pCLSID`  
 指向要注册的对象的 CLSID。 如果为 NULL，将注册在对象映射中的所有对象。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 `AtlComModuleRegisterServer`指导 ATL 自动生成对象映射和映射中注册的每个对象。 如果`pCLSID`不可为 NULL，则引用的对象`pCLSID`注册; 否则为注册的所有对象。  
  
 调用此函数[CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver)。  
  
##  <a name="a-nameatlcommoduleunregisterservera--atlcommoduleunregisterserver"></a><a name="atlcommoduleunregisterserver"></a>AtlComModuleUnregisterServer  
 调用此函数可在对象映射中注销所有对象。  
  
```
ATLINLINE ATLAPI AtlComModuleUnregisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID);
```  
  
### <a name="parameters"></a>参数  
 `pComModule`  
 对 COM 模块的指针。  
  
 `bUnRegTypeLib`  
 如果要注册类型库，则为 TRUE。  
  
 `pCLSID`  
 指向要取消注册的对象的 CLSID。 如果为 NULL 对象映射中的所有对象都将注销。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 `AtlComModuleUnregisterServer`将遍历 ATL 对象映射并注销映射中的每个对象。 如果`pCLSID`为 NULL，则引用的对象不是`pCLSID`注销; 否则为所有对象都是未注册。  
  
 调用此函数[CAtlComModule::UnregisterServer](catlcommodule-class.md#unregisterserver)。  
  
##  <a name="a-nameatlcommoduleregisterclassobjectsa--atlcommoduleregisterclassobjects"></a><a name="atlcommoduleregisterclassobjects"></a>AtlComModuleRegisterClassObjects  
 调用此函数可注册类对象。  
  
```
ATLINLINE ATLAPI AtlComModuleRegisterClassObjects(
    _ATL_COM_MODULE* pComModule,
    DWORD dwClsContext,
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>参数  
 `pComModule`  
 对 COM 模块的指针。  
  
 `dwClsContext`  
 指定的类对象将在其中运行的上下文。 可能值包括 CLSCTX_INPROC_SERVER、 CLSCTX_INPROC_HANDLER 或 CLSCTX_LOCAL_SERVER。 请参阅[CLSCTX](http://msdn.microsoft.com/library/windows/desktop/ms693716)的更多详细信息。  
  
 `dwFlags`  
 确定对类对象的连接类型。 可能值包括 REGCLS_SINGLEUSE、 REGCLS_MULTIPLEUSE 或 REGCLS_MULTI_SEPARATE。 请参阅[结合指定](http://msdn.microsoft.com/library/windows/desktop/ms679697)的更多详细信息。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 利用此帮助器函数[CComModule::RegisterClassObjects](ccommodule-class.md#registerclassobjects) （ATL 7.0 中已过时） 和[CAtlExeModuleT::RegisterClassObjects](catlexemodulet-class.md#registerclassobjects)。  
  
##  <a name="a-nameatlcommodulerevokeclassobjectsa--atlcommodulerevokeclassobjects"></a><a name="atlcommodulerevokeclassobjects"></a>AtlComModuleRevokeClassObjects  
 调用此函数可从运行对象表中移除类工厂。  
  
```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```  
  
### <a name="parameters"></a>参数  
 `pComModule`  
 对 COM 模块的指针。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 利用此帮助器函数[CComModule::RevokeClassObjects](ccommodule-class.md#revokeclassobjects) （ATL 7.0 中已过时） 和[CAtlExeModuleT::RevokeClassObjects](catlexemodulet-class.md#revokeclassobjects)。  
  
##  <a name="a-nameatlcommodulegetclassobjecta--atlcommodulegetclassobject"></a><a name="atlcommodulegetclassobject"></a>AtlComModuleGetClassObject  
 调用此函数可返回类工厂。  
  
```
ATLINLINE ATLAPI AtlComModuleGetClassObject(
    _ATL_COM_MODULE* pComModule,
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv);
```  
  
### <a name="parameters"></a>参数  
 `pComModule`  
 对 COM 模块的指针。  
  
 `rclsid`  
 要创建对象的 CLSID。  
  
 `riid`  
 所请求的接口的 IID。  
  
 `ppv`  
 指向由标识的接口指针的指针`riid`。 如果该对象不支持此接口，`ppv`设置为 NULL。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 利用此帮助器函数[CComModule::GetClassObject](ccommodule-class.md#getclassobject) （ATL 7.0 中已过时） 和[CAtlDllModuleT::GetClassObject](catldllmodulet-class.md#getclassobject)。  
  
## <a name="see-also"></a>另请参阅  
 [函数](../../atl/reference/atl-functions.md)

