---
title: "COleObjectFactory 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleObjectFactory
- AFXDISP/COleObjectFactory
- AFXDISP/COleObjectFactory::COleObjectFactory
- AFXDISP/COleObjectFactory::GetClassID
- AFXDISP/COleObjectFactory::IsLicenseValid
- AFXDISP/COleObjectFactory::IsRegistered
- AFXDISP/COleObjectFactory::Register
- AFXDISP/COleObjectFactory::RegisterAll
- AFXDISP/COleObjectFactory::Revoke
- AFXDISP/COleObjectFactory::RevokeAll
- AFXDISP/COleObjectFactory::UnregisterAll
- AFXDISP/COleObjectFactory::UpdateRegistry
- AFXDISP/COleObjectFactory::UpdateRegistryAll
- AFXDISP/COleObjectFactory::GetLicenseKey
- AFXDISP/COleObjectFactory::OnCreateObject
- AFXDISP/COleObjectFactory::VerifyLicenseKey
- AFXDISP/COleObjectFactory::VerifyUserLicense
dev_langs:
- C++
helpviewer_keywords:
- OLE, class factory
- OLE class factory
- COleObjectFactory class
- objects [C++], creating OLE
- OLE objects
- object creation, OLE objects
- class factories, COleObjectFactory class
- OLE objects, creating
ms.assetid: ab179c1e-4af2-44aa-a576-37c48149b427
caps.latest.revision: 21
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
ms.openlocfilehash: 643d17ccdefb60b561e7e5488753a6dbf778c69f
ms.lasthandoff: 02/24/2017

---
# <a name="coleobjectfactory-class"></a>COleObjectFactory 类
实现 OLE 类工厂，此工厂创建服务器、自动化对象和文档等 OLE 对象。  
  
## <a name="syntax"></a>语法  
  
```  
class COleObjectFactory : public CCmdTarget  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COleObjectFactory::COleObjectFactory](#coleobjectfactory)|构造 `COleObjectFactory` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[COleObjectFactory::GetClassID](#getclassid)|返回 OLE 类的此工厂创建的对象的 ID。|  
|[COleObjectFactory::IsLicenseValid](#islicensevalid)|确定控件的许可证是否有效。|  
|[COleObjectFactory::IsRegistered](#isregistered)|指示是否向 OLE 系统 Dll 注册的对象工厂。|  
|[真](#register)|使用 OLE 系统 Dll 注册此对象工厂。|  
|[COleObjectFactory::RegisterAll](#registerall)|使用 OLE 系统 Dll 中注册所有应用程序的对象工厂。|  
|[COleObjectFactory::Revoke](#revoke)|撤消向 OLE 系统 Dll 此对象工厂的注册。|  
|[COleObjectFactory::RevokeAll](#revokeall)|撤消向 OLE 系统 Dll 的应用程序的对象工厂登记。|  
|[COleObjectFactory::UnregisterAll](#unregisterall)|取消注册所有应用程序的对象工厂。|  
|[COleObjectFactory::UpdateRegistry](#updateregistry)|向 OLE 系统注册表中注册此对象工厂。|  
|[COleObjectFactory::UpdateRegistryAll](#updateregistryall)|向 OLE 系统注册表中注册所有应用程序的对象工厂。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[COleObjectFactory::GetLicenseKey](#getlicensekey)|从控件的 DLL 中请求的唯一键。|  
|[COleObjectFactory::OnCreateObject](#oncreateobject)|由框架来创建一个新对象，此工厂的类型调用。|  
|[COleObjectFactory::VerifyLicenseKey](#verifylicensekey)|验证密钥嵌入在控件中嵌入在容器中的键相匹配。|  
|[COleObjectFactory::VerifyUserLicense](#verifyuserlicense)|验证控件已授权供设计时使用。|  
  
## <a name="remarks"></a>备注  
 `COleObjectFactory`类具有以下成员功能执行以下功能︰  
  
-   管理注册的对象。  
  
-   正在更新 OLE 系统注册，以及运行时注册，以通知 OLE 对象正在运行，并准备好接收消息。  
  
-   强制通过限制控件向许可开发人员在设计时和在运行时授权应用程序的使用许可。  
  
-   向 OLE 系统注册表中注册控件对象工厂。  
  
 有关创建对象的详细信息，请参阅文章[数据对象和数据源 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)和[数据对象和数据源︰ 创建和销毁](../../mfc/data-objects-and-data-sources-creation-and-destruction.md)。 有关注册的详细信息，请参阅文章[注册](../../mfc/registration.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleObjectFactory`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdisp.h  
  
##  <a name="coleobjectfactory"></a>COleObjectFactory::COleObjectFactory  
 构造`COleObjectFactory`对象，作为未注册的对象工厂，对其进行初始化，并将其添加到工厂的列表。  
  
```  
COleObjectFactory(
    REFCLSID clsid,  
    CRuntimeClass* pRuntimeClass,  
    BOOL bMultiInstance,  
    LPCTSTR lpszProgID);

 
COleObjectFactory(
    REFCLSID clsid,  
    CRuntimeClass* pRuntimeClass,  
    BOOL bMultiInstance,  
    int nFlags,  
    LPCTSTR lpszProgID);
```  
  
### <a name="parameters"></a>参数  
 `clsid`  
 对此对象工厂表示的 OLE 类 ID 的引用。  
  
 `pRuntimeClass`  
 向此工厂可以创建的 c + + 对象的运行时类的指针。  
  
 `bMultiInstance`  
 指示应用程序的单个实例是否可以支持多个实例化。 如果**TRUE**，为每个请求创建的对象启动该应用程序的多个实例。  
  
 `nFlags`  
 包含一个或多个以下标志︰  
  
- **afxRegDefault**将线程模型设置为 ThreadingModel = 单元。  
  
- **afxRegInsertable**使控件可以显示在**插入对象**OLE 对象的对话框。  
  
- `afxRegApartmentThreading`ThreadingModel 注册表中设置线程模型 = 单元。  
  
- **afxRegFreeThreading** ThreadingModel 注册表中设置线程模型 = 免费。  
  
     您可以组合使用两个标记`afxRegApartmentThreading`和`afxRegFreeThreading`设置 ThreadingModel = Both。 请参阅[InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关线程处理模型注册的详细信息。  
  
 `lpszProgID`  
 包含口头程序的标识符，如"Microsoft Excel。"的字符串的指针  
  
### <a name="remarks"></a>备注  
 若要使用该对象，但是，您必须注册它。  
  
 有关详细信息，请参阅[CLSID 项](http://msdn.microsoft.com/library/windows/desktop/ms691424)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getclassid"></a>COleObjectFactory::GetClassID  
 返回此工厂表示的 OLE 类 ID 的引用。  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>返回值  
 表示对 OLE 类 ID 此工厂的引用。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[CLSID 项](http://msdn.microsoft.com/library/windows/desktop/ms691424)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getlicensekey"></a>COleObjectFactory::GetLicenseKey  
 从控件的 DLL 中请求的唯一的许可证密钥并将其存储在`BSTR`指向`pbstrKey`。  
  
```  
virtual BOOL GetLicenseKey(
    DWORD dwReserved,  
    BSTR* pbstrKey);
```  
  
### <a name="parameters"></a>参数  
 `dwReserved`  
 留待将来使用。  
  
 `pbstrKey`  
 指向`BSTR`将存储的许可证密钥。  
  
### <a name="return-value"></a>返回值  
 如果许可证密钥字符串不是，则为非**NULL**; 否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现返回 0 并将存储在中为 nothing `BSTR`。 如果您使用 MFC ActiveX 控件向导创建您的项目，controlwizard 可提供一个替代以检索该控件的许可证密钥。  
  
##  <a name="islicensevalid"></a>COleObjectFactory::IsLicenseValid  
 确定控件的许可证是否有效。  
  
```  
BOOL IsLicenseValid();
```  
  
### <a name="return-value"></a>返回值  
 True successul;否则为 false。  
  
##  <a name="isregistered"></a>COleObjectFactory::IsRegistered  
 返回一个非零值，如果向 OLE 系统 Dll 注册工厂。  
  
```  
virtual BOOL IsRegistered() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果出厂注册，则非零值否则为 0。  
  
##  <a name="oncreateobject"></a>COleObjectFactory::OnCreateObject  
 由框架来创建一个新的对象调用。  
  
```  
virtual CCmdTarget* OnCreateObject();
```  
  
### <a name="return-value"></a>返回值  
 指向所创建的对象的指针。 如果该操作失败，它可以引发内存异常。  
  
### <a name="remarks"></a>备注  
 重写此函数可从某些对象而不创建对象[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)传递给构造函数。  
  
##  <a name="register"></a>真  
 使用 OLE 系统 Dll 注册此对象工厂。  
  
```  
virtual BOOL Register();
```  
  
### <a name="return-value"></a>返回值  
 如果成功注册工厂则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 通常调用此函数[cwinapp:: Initinstance](../../mfc/reference/cwinapp-class.md#initinstance)启动应用程序。  
  
##  <a name="registerall"></a>COleObjectFactory::RegisterAll  
 使用 OLE 系统 Dll 中注册所有应用程序的对象工厂。  
  
```  
static BOOL PASCAL RegisterAll();
```  
  
### <a name="return-value"></a>返回值  
 如果成功注册工厂则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 通常调用此函数[cwinapp:: Initinstance](../../mfc/reference/cwinapp-class.md#initinstance)启动应用程序。  
  
##  <a name="revoke"></a>COleObjectFactory::Revoke  
 撤消向 OLE 系统 Dll 此对象工厂的注册。  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>备注  
 应用程序终止前，框架将自动调用此函数。 如有必要，从调用它的重写[CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)。  
  
##  <a name="revokeall"></a>COleObjectFactory::RevokeAll  
 撤消所有向 OLE 系统 Dll 的应用程序的对象工厂登记。  
  
```  
static void PASCAL RevokeAll();
```  
  
### <a name="remarks"></a>备注  
 应用程序终止前，框架将自动调用此函数。 如有必要，从调用它的重写[CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)。  
  
##  <a name="unregisterall"></a>COleObjectFactory::UnregisterAll  
 取消注册所有应用程序的对象工厂。  
  
```  
static BOOL PASCAL UnregisterAll();
```  
  
### <a name="return-value"></a>返回值  
 若成功，则为 TRUE；否则为 FALSE。  
  
##  <a name="updateregistry"></a>COleObjectFactory::UpdateRegistry  
 向 OLE 系统注册表中注册所有应用程序的对象工厂。  
  
```  
void UpdateRegistry(LPCTSTR lpszProgID = NULL);  
virtual BOOL UpdateRegistry(BOOL bRegister);
```  
  
### <a name="parameters"></a>参数  
 `lpszProgID`  
 包含用户可读程序的标识符，如"Excel.Document.5。"的字符串的指针  
  
 `bRegister`  
 确定是否要注册的控件类对象工厂。  
  
### <a name="remarks"></a>备注  
 请按照下面的讨论，此函数的两种形式的操作︰  
  
- **UpdateRegistry (** `lpszProgID` **)**向 OLE 系统注册表中注册此对象工厂。 通常调用此函数[cwinapp:: Initinstance](../../mfc/reference/cwinapp-class.md#initinstance)启动应用程序。  
  
- **UpdateRegistry (** `bRegister` **)**这种形式的函数是可重写。 如果`bRegister`是**TRUE**，此函数与系统注册表中注册的控件类。 否则，取消注册类。  
  
     如果您使用 MFC ActiveX 控件向导创建您的项目，controlwizard 可提供此纯虚函数的重写。  
  
##  <a name="updateregistryall"></a>COleObjectFactory::UpdateRegistryAll  
 向 OLE 系统注册表中注册所有应用程序的对象工厂。  
  
```  
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bRegister`  
 确定是否要注册的控件类对象工厂。  
  
### <a name="return-value"></a>返回值  
 如果已成功更新工厂; 则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 通常调用此函数[cwinapp:: Initinstance](../../mfc/reference/cwinapp-class.md#initinstance)启动应用程序。  
  
##  <a name="verifylicensekey"></a>COleObjectFactory::VerifyLicenseKey  
 确认该容器已获得授权才能使用 OLE 控件。  
  
```  
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```  
  
### <a name="parameters"></a>参数  
 `bstrKey`  
 一个`BSTR`存储容器的版本的许可字符串。  
  
### <a name="return-value"></a>返回值  
 如果运行时许可证为有效，则为非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 默认版本调用[GetLicenseKey](#getlicensekey)获取控件的一个副本的许可字符串并将它与中的字符串进行比较`bstrKey`。 如果两个字符串匹配，则函数返回一个非零值;否则返回 0。  
  
 您可以重写此函数可提供许可证的自定义的验证。  
  
 该函数[VerifyUserLicense](#verifyuserlicense)验证设计时许可证。  
  
##  <a name="verifyuserlicense"></a>COleObjectFactory::VerifyUserLicense  
 验证 OLE 控件的设计时许可证。  
  
```  
virtual BOOL VerifyUserLicense();
```  
  
### <a name="return-value"></a>返回值  
 如果设计时许可证为有效，则为非零值否则为 0。  
  
## <a name="see-also"></a>另请参阅  
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleTemplateServer 类](../../mfc/reference/coletemplateserver-class.md)

