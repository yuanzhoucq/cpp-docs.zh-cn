---
title: COleObjectFactory 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 22805550d13ecb400b151495363e5eda2dfb3b76
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503743"
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
|[COleObjectFactory::GetClassID](#getclassid)|返回此工厂创建的对象的 OLE 类 ID。|
|[COleObjectFactory::IsLicenseValid](#islicensevalid)|确定控件的许可证是否有效。|
|[COleObjectFactory::IsRegistered](#isregistered)|指示是否已向 OLE 系统 Dll 注册对象工厂。|
|[COleObjectFactory::Register](#register)|向 OLE 系统 Dll 注册此对象工厂。|
|[COleObjectFactory::RegisterAll](#registerall)|用 OLE 系统 Dll 注册应用程序的所有对象工厂。|
|[COleObjectFactory::Revoke](#revoke)|用 OLE 系统 Dll 撤消该对象工厂的注册。|
|[COleObjectFactory::RevokeAll](#revokeall)|使用 OLE 系统 Dll 撤消应用程序对象工厂的注册。|
|[COleObjectFactory::UnregisterAll](#unregisterall)|注销应用程序的所有对象工厂。|
|[COleObjectFactory::UpdateRegistry](#updateregistry)|向 OLE 系统注册表注册此对象工厂。|
|[COleObjectFactory::UpdateRegistryAll](#updateregistryall)|将所有应用程序的对象工厂注册到 OLE 系统注册表中。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[COleObjectFactory::GetLicenseKey](#getlicensekey)|从控件的 DLL 请求一个唯一键。|
|[COleObjectFactory::OnCreateObject](#oncreateobject)|由框架调用以创建此工厂的类型的新对象。|
|[COleObjectFactory::VerifyLicenseKey](#verifylicensekey)|验证控件中嵌入的键是否与容器中嵌入的键相匹配。|
|[COleObjectFactory::VerifyUserLicense](#verifyuserlicense)|验证控件是否已获得设计时使用的许可。|

## <a name="remarks"></a>备注

`COleObjectFactory`类具有用于执行以下函数的成员函数:

- 管理对象的注册。

- 更新 OLE 系统注册, 以及通知 OLE 对象正在运行并准备好接收消息的运行时注册。

- 通过在设计时将控件限制为授权开发人员, 并在运行时将控件限制为许可的应用程序, 强制实施授权。

- 向 OLE 系统注册表注册控件对象工厂。

有关创建对象的详细信息, 请参阅文章[数据对象和数据源 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)和[数据对象和数据源:创建和销毁](../../mfc/data-objects-and-data-sources-creation-and-destruction.md)。 有关注册的详细信息, 请参阅文章[注册](../../mfc/registration.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleObjectFactory`

## <a name="requirements"></a>要求

**标头：** afxdisp.h

##  <a name="coleobjectfactory"></a>  COleObjectFactory::COleObjectFactory

构造一个`COleObjectFactory`对象, 将其初始化为未注册的对象工厂, 并将其添加到工厂列表。

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

*clsid*<br/>
对此对象工厂表示的 OLE 类 ID 的引用。

*pRuntimeClass*<br/>
指向此工厂可以创建的C++对象的运行时类的指针。

*bMultiInstance*<br/>
指示应用程序的单个实例是否可以支持多个实例化。 如果为 TRUE, 则为每个请求启动应用程序的多个实例, 以创建对象。

*nFlags*<br/>
包含一个或多个以下标志:

- `afxRegDefault`将线程模型设置为 ThreadingModel = 单元。

- `afxRegInsertable`允许控件显示在 OLE 对象的 "**插入对象**" 对话框中。

- `afxRegApartmentThreading`将注册表中的线程模型设置为 ThreadingModel = 单元。

- `afxRegFreeThreading`将注册表中的线程模型设置为 ThreadingModel = Free。

   可以合并这两个标志`afxRegApartmentThreading` , `afxRegFreeThreading`并设置 ThreadingModel = Both。 有关线程模型注册的详细信息, 请参阅 Windows SDK 中的[InprocServer32](/windows/win32/com/inprocserver32) 。

*lpszProgID*<br/>
指向包含口头程序标识符 (如 "Microsoft Excel") 的字符串的指针。

### <a name="remarks"></a>备注

但是, 若要使用该对象, 必须进行注册。

有关详细信息, 请参阅 Windows SDK 中的[CLSID 关键字](/windows/win32/com/clsid-key-hklm)。

##  <a name="getclassid"></a>COleObjectFactory:: GetClassID

返回一个对此工厂表示的 OLE 类 ID 的引用。

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>返回值

对此工厂表示的 OLE 类 ID 的引用。

### <a name="remarks"></a>备注

有关详细信息, 请参阅 Windows SDK 中的[CLSID 关键字](/windows/win32/com/clsid-key-hklm)。

##  <a name="getlicensekey"></a>COleObjectFactory:: GetLicenseKey

从控件的 DLL 请求一个唯一许可证密钥, 并将其存储在*pbstrKey*所指向的 BSTR 中。

```
virtual BOOL GetLicenseKey(
    DWORD dwReserved,
    BSTR* pbstrKey);
```

### <a name="parameters"></a>参数

*dwReserved*<br/>
留待将来使用。

*pbstrKey*<br/>
指向将存储许可证密钥的 BSTR 的指针。

### <a name="return-value"></a>返回值

如果许可证密钥字符串不为 NULL, 则为非零值;否则为0。

### <a name="remarks"></a>备注

此函数的默认实现将返回 0, 并且不会在 BSTR 中存储任何内容。 如果使用 MFC ActiveX ControlWizard 创建项目, ControlWizard 会提供一个用于检索控件许可证密钥的替代。

##  <a name="islicensevalid"></a>COleObjectFactory:: IsLicenseValid

确定控件的许可证是否有效。

```
BOOL IsLicenseValid();
```

### <a name="return-value"></a>返回值

如果 successul, 则为 TRUE;否则为 false。

##  <a name="isregistered"></a>COleObjectFactory:: IsRegistered

如果向 OLE 系统 Dll 注册了工厂, 则返回一个非零值。

```
virtual BOOL IsRegistered() const;
```

### <a name="return-value"></a>返回值

如果已注册工厂, 则为非零值;否则为0。

##  <a name="oncreateobject"></a>  COleObjectFactory::OnCreateObject

由框架调用, 用于创建新的对象。

```
virtual CCmdTarget* OnCreateObject();
```

### <a name="return-value"></a>返回值

指向已创建对象的指针。 如果失败, 它可能引发内存异常。

### <a name="remarks"></a>备注

重写此函数, 以从传递给构造函数的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)以外的内容创建对象。

##  <a name="register"></a>  COleObjectFactory::Register

向 OLE 系统 Dll 注册此对象工厂。

```
virtual BOOL Register();
```

### <a name="return-value"></a>返回值

如果成功注册工厂, 则为非零值;否则为0。

### <a name="remarks"></a>备注

当应用程序启动时, 此函数通常由[CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)调用。

##  <a name="registerall"></a>  COleObjectFactory::RegisterAll

用 OLE 系统 Dll 注册应用程序的所有对象工厂。

```
static BOOL PASCAL RegisterAll();
```

### <a name="return-value"></a>返回值

如果成功注册工厂, 则为非零值;否则为0。

### <a name="remarks"></a>备注

当应用程序启动时, 此函数通常由[CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)调用。

##  <a name="revoke"></a>  COleObjectFactory::Revoke

用 OLE 系统 Dll 撤消该对象工厂的注册。

```
void Revoke();
```

### <a name="remarks"></a>备注

框架在应用程序终止之前自动调用此函数。 如有必要, 请从[CWinApp:: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)的重写调用它。

##  <a name="revokeall"></a>  COleObjectFactory::RevokeAll

通过 OLE 系统 Dll 撤消应用程序的所有对象工厂的注册。

```
static void PASCAL RevokeAll();
```

### <a name="remarks"></a>备注

框架在应用程序终止之前自动调用此函数。 如有必要, 请从[CWinApp:: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)的重写调用它。

##  <a name="unregisterall"></a>  COleObjectFactory::UnregisterAll

注销应用程序的所有对象工厂。

```
static BOOL PASCAL UnregisterAll();
```

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

##  <a name="updateregistry"></a>COleObjectFactory:: UpdateRegistry

将所有应用程序的对象工厂注册到 OLE 系统注册表中。

```
void UpdateRegistry(LPCTSTR lpszProgID = NULL);
virtual BOOL UpdateRegistry(BOOL bRegister);
```

### <a name="parameters"></a>参数

*lpszProgID*<br/>
指向字符串的指针, 该字符串包含可读的程序标识符, 如 "

*bRegister*<br/>
确定是否要注册控件类的对象工厂。

### <a name="remarks"></a>备注

此函数的两种形式的简要讨论如下:

- **UpdateRegistry (** `lpszProgID` **)** 将此对象工厂注册到 OLE 系统注册表。 当应用程序启动时, 此函数通常由[CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)调用。

- **UpdateRegistry (** `bRegister` **)** 这种形式的函数是可重写的。 如果*bRegister*为 TRUE, 则此函数会向系统注册表注册 control 类。 否则, 将取消注册类。

   如果使用 MFC ActiveX ControlWizard 创建项目, ControlWizard 将向此纯虚函数提供重写。

##  <a name="updateregistryall"></a>COleObjectFactory:: UpdateRegistryAll

将所有应用程序的对象工厂注册到 OLE 系统注册表中。

```
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```

### <a name="parameters"></a>参数

*bRegister*<br/>
确定是否要注册控件类的对象工厂。

### <a name="return-value"></a>返回值

如果成功更新了工厂, 则为非零值;否则为0。

### <a name="remarks"></a>备注

当应用程序启动时, 此函数通常由[CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)调用。

##  <a name="verifylicensekey"></a>COleObjectFactory:: VerifyLicenseKey

验证是否已授权容器使用 OLE 控件。

```
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```

### <a name="parameters"></a>参数

*bstrKey*<br/>
存储容器的许可证字符串版本的 BSTR。

### <a name="return-value"></a>返回值

如果运行时许可证有效, 则为非零值;否则为0。

### <a name="remarks"></a>备注

默认版本调用[GetLicenseKey](#getlicensekey)来获取控件的许可证字符串的副本, 并将其与*bstrKey*中的字符串进行比较。 如果两个字符串匹配, 该函数将返回一个非零值;否则, 返回0。

您可以重写此函数以提供对许可证的自定义验证。

函数[VerifyUserLicense](#verifyuserlicense)用于验证设计时许可证。

##  <a name="verifyuserlicense"></a>COleObjectFactory:: VerifyUserLicense

验证 OLE 控件的设计时许可证。

```
virtual BOOL VerifyUserLicense();
```

### <a name="return-value"></a>返回值

如果设计时许可证有效, 则为非零值;否则为0。

## <a name="see-also"></a>请参阅

[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleTemplateServer 类](../../mfc/reference/coletemplateserver-class.md)
