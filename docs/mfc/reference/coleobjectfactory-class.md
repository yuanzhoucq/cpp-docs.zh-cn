---
title: COleObjectFactory 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- COleObjectFactory [MFC], COleObjectFactory
- COleObjectFactory [MFC], GetClassID
- COleObjectFactory [MFC], IsLicenseValid
- COleObjectFactory [MFC], IsRegistered
- COleObjectFactory [MFC], Register
- COleObjectFactory [MFC], RegisterAll
- COleObjectFactory [MFC], Revoke
- COleObjectFactory [MFC], RevokeAll
- COleObjectFactory [MFC], UnregisterAll
- COleObjectFactory [MFC], UpdateRegistry
- COleObjectFactory [MFC], UpdateRegistryAll
- COleObjectFactory [MFC], GetLicenseKey
- COleObjectFactory [MFC], OnCreateObject
- COleObjectFactory [MFC], VerifyLicenseKey
- COleObjectFactory [MFC], VerifyUserLicense
ms.assetid: ab179c1e-4af2-44aa-a576-37c48149b427
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd68493c9be5eb0bff63504cf49b38b9a2f216d4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375932"
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
  
|名称|描述|  
|----------|-----------------|  
|[COleObjectFactory::GetClassID](#getclassid)|返回 OLE 类的此工厂创建的对象的 ID。|  
|[COleObjectFactory::IsLicenseValid](#islicensevalid)|确定控件的许可证是否有效。|  
|[COleObjectFactory::IsRegistered](#isregistered)|指示是否使用 OLE 系统 Dll 注册对象的工厂。|  
|[COleObjectFactory::Register](#register)|使用 OLE 系统 Dll 中注册此对象工厂。|  
|[COleObjectFactory::RegisterAll](#registerall)|使用 OLE 系统 Dll 中注册所有应用程序的对象工厂。|  
|[COleObjectFactory::Revoke](#revoke)|撤消向 OLE 系统 Dll 此对象工厂注册。|  
|[COleObjectFactory::RevokeAll](#revokeall)|撤消具有 OLE 系统 Dll 的应用程序的对象工厂的注册。|  
|[COleObjectFactory::UnregisterAll](#unregisterall)|注销所有应用程序的对象工厂。|  
|[COleObjectFactory::UpdateRegistry](#updateregistry)|向 OLE 系统注册表中注册此对象工厂。|  
|[COleObjectFactory::UpdateRegistryAll](#updateregistryall)|向 OLE 系统注册表中注册所有应用程序的对象工厂。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleObjectFactory::GetLicenseKey](#getlicensekey)|从控件的 DLL 中请求的唯一键。|  
|[COleObjectFactory::OnCreateObject](#oncreateobject)|由框架调用以创建此工厂的类型的新对象。|  
|[COleObjectFactory::VerifyLicenseKey](#verifylicensekey)|验证在控件中嵌入的密钥与嵌入在容器中的键匹配。|  
|[COleObjectFactory::VerifyUserLicense](#verifyuserlicense)|验证控件已授权的设计时使用。|  
  
## <a name="remarks"></a>备注  
 `COleObjectFactory`类具有的成员函数，用于在执行以下功能：  
  
-   管理对象的注册。  
  
-   正在更新 OLE 系统注册，以及运行时注册，以通知 OLE 对象运行并准备好接收消息。  
  
-   强制实施通过限制控制到许可的开发人员在设计时和许可的应用程序在运行时使用的授权。  
  
-   向 OLE 系统注册表中注册控件对象工厂。  
  
 有关创建对象的详细信息，请参阅文章[数据对象和数据源 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)和[数据对象和数据源： 创建和析构](../../mfc/data-objects-and-data-sources-creation-and-destruction.md)。 有关注册的详细信息，请参阅文章[注册](../../mfc/registration.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleObjectFactory`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdisp.h  
  
##  <a name="coleobjectfactory"></a>  COleObjectFactory::COleObjectFactory  
 构造`COleObjectFactory`对象，作为未注册的对象工厂，对其进行初始化，并将其添加到列表的工厂。  
  
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
 对此对象工厂表示 OLE 类 ID 的引用。  
  
 `pRuntimeClass`  
 指向此工厂可以创建的 c + + 对象的运行时类的指针。  
  
 `bMultiInstance`  
 指示应用程序的单个实例是否可以支持多个实例化。 如果**TRUE**，为每个请求，以创建对象启动的应用程序的多个实例。  
  
 `nFlags`  
 包含一个或多个以下的标志：  
  
- **afxRegDefault**将线程模型设置为 ThreadingModel = 单元。  
  
- **afxRegInsertable**允许控件中显示**插入对象**OLE 对象的对话框。  
  
- `afxRegApartmentThreading` ThreadingModel 到注册表中设置线程模型 = 单元。  
  
- **afxRegFreeThreading** ThreadingModel 到注册表中设置线程模型 = 免费。  
  
     你可以组合两个标志`afxRegApartmentThreading`和`afxRegFreeThreading`设置 ThreadingModel = Both。 请参阅[InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390)线程处理模型注册的详细信息的 Windows SDK 中。  
  
 `lpszProgID`  
 指向字符串，该字符串包含一个文字程序标识符，例如"Microsoft Excel。"  
  
### <a name="remarks"></a>备注  
 若要使用该对象，但是，您必须注册它。  
  
 有关详细信息，请参阅[CLSID 项](http://msdn.microsoft.com/library/windows/desktop/ms691424)Windows SDK 中。  
  
##  <a name="getclassid"></a>  COleObjectFactory::GetClassID  
 返回此工厂表示的 OLE 类 ID 的引用。  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>返回值  
 表示对 OLE 类 ID 此工厂的引用。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[CLSID 项](http://msdn.microsoft.com/library/windows/desktop/ms691424)Windows SDK 中。  
  
##  <a name="getlicensekey"></a>  COleObjectFactory::GetLicenseKey  
 从控件的 DLL 中请求的唯一许可密钥并将其存储在`BSTR`指向`pbstrKey`。  
  
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
 如果许可证密钥字符串不是零**NULL**; 否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现返回 0，并将存储在中为 nothing `BSTR`。 如果您使用 MFC ActiveX 控件向导创建你的项目，controlwizard 可提供检索控件的许可证密钥的替代。  
  
##  <a name="islicensevalid"></a>  COleObjectFactory::IsLicenseValid  
 确定控件的许可证是否有效。  
  
```  
BOOL IsLicenseValid();
```  
  
### <a name="return-value"></a>返回值  
 True successul;否则为 false。  
  
##  <a name="isregistered"></a>  COleObjectFactory::IsRegistered  
 如果使用 OLE 系统 Dll 注册的工厂，则返回非零值。  
  
```  
virtual BOOL IsRegistered() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果注册工厂; 则为非 0否则为 0。  
  
##  <a name="oncreateobject"></a>  COleObjectFactory::OnCreateObject  
 由框架调用以创建新的对象。  
  
```  
virtual CCmdTarget* OnCreateObject();
```  
  
### <a name="return-value"></a>返回值  
 指向所创建的对象的指针。 如果失败，它可以引发内存异常。  
  
### <a name="remarks"></a>备注  
 重写此函数可从某些对象而不创建对象[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)传递到构造函数。  
  
##  <a name="register"></a>  COleObjectFactory::Register  
 使用 OLE 系统 Dll 中注册此对象工厂。  
  
```  
virtual BOOL Register();
```  
  
### <a name="return-value"></a>返回值  
 如果成功注册的工厂; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 通常调用此函数[CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)当启动应用程序。  
  
##  <a name="registerall"></a>  COleObjectFactory::RegisterAll  
 使用 OLE 系统 Dll 中注册所有应用程序的对象工厂。  
  
```  
static BOOL PASCAL RegisterAll();
```  
  
### <a name="return-value"></a>返回值  
 如果成功注册工厂; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 通常调用此函数[CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)当启动应用程序。  
  
##  <a name="revoke"></a>  COleObjectFactory::Revoke  
 撤消向 OLE 系统 Dll 此对象工厂注册。  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>备注  
 在应用程序终止之前，框架将自动调用此函数。 如有必要，调用的重写[CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)。  
  
##  <a name="revokeall"></a>  COleObjectFactory::RevokeAll  
 撤消所有具有 OLE 系统 Dll 的应用程序的对象工厂的注册。  
  
```  
static void PASCAL RevokeAll();
```  
  
### <a name="remarks"></a>备注  
 在应用程序终止之前，框架将自动调用此函数。 如有必要，调用的重写[CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)。  
  
##  <a name="unregisterall"></a>  COleObjectFactory::UnregisterAll  
 注销所有应用程序的对象工厂。  
  
```  
static BOOL PASCAL UnregisterAll();
```  
  
### <a name="return-value"></a>返回值  
 若成功，则为 TRUE；否则为 FALSE。  
  
##  <a name="updateregistry"></a>  COleObjectFactory::UpdateRegistry  
 向 OLE 系统注册表中注册所有应用程序的对象工厂。  
  
```  
void UpdateRegistry(LPCTSTR lpszProgID = NULL);  
virtual BOOL UpdateRegistry(BOOL bRegister);
```  
  
### <a name="parameters"></a>参数  
 `lpszProgID`  
 指向字符串，该字符串包含的用户可读的程序标识符，如"Excel.Document.5"。  
  
 `bRegister`  
 确定是否要注册的控件类的对象工厂。  
  
### <a name="remarks"></a>备注  
 请按照下面的讨论，此函数的两个窗体的操作：  
  
- **UpdateRegistry (** `lpszProgID` **)** OLE 系统注册表中注册此对象工厂。 通常调用此函数[CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)当启动应用程序。  
  
- **UpdateRegistry (** `bRegister` **)** 这种形式的函数是可重写。 如果`bRegister`是**TRUE**，此函数向系统注册表中注册的控件类。 否则，它注销类。  
  
     如果您使用 MFC ActiveX 控件向导创建你的项目，controlwizard 可提供此纯虚函数的重写。  
  
##  <a name="updateregistryall"></a>  COleObjectFactory::UpdateRegistryAll  
 向 OLE 系统注册表中注册所有应用程序的对象工厂。  
  
```  
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bRegister`  
 确定是否要注册的控件类的对象工厂。  
  
### <a name="return-value"></a>返回值  
 如果已成功更新工厂; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 通常调用此函数[CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)当启动应用程序。  
  
##  <a name="verifylicensekey"></a>  COleObjectFactory::VerifyLicenseKey  
 验证容器已获许可使用 OLE 控件。  
  
```  
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```  
  
### <a name="parameters"></a>参数  
 `bstrKey`  
 A`BSTR`存储容器的版本的许可证字符串。  
  
### <a name="return-value"></a>返回值  
 如果运行时许可证为有效，则为非零否则为 0。  
  
### <a name="remarks"></a>备注  
 默认版本调用[GetLicenseKey](#getlicensekey)若要获取的控件副本的许可证字符串并将它与中的字符串进行比较`bstrKey`。 如果两个字符串匹配，则函数返回一个非零值;否则，返回 0。  
  
 你可以重写此函数可提供许可证的自定义的验证。  
  
 该函数[VerifyUserLicense](#verifyuserlicense)验证设计时许可证。  
  
##  <a name="verifyuserlicense"></a>  COleObjectFactory::VerifyUserLicense  
 验证 OLE 控件的设计时许可证。  
  
```  
virtual BOOL VerifyUserLicense();
```  
  
### <a name="return-value"></a>返回值  
 如果设计时许可证为有效，则为非零否则为 0。  
  
## <a name="see-also"></a>请参阅  
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleTemplateServer 类](../../mfc/reference/coletemplateserver-class.md)
