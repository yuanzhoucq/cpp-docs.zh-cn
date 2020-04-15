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
ms.openlocfilehash: 9f3d86cf735c02b6021441c66d9fd64547f6d6c2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374907"
---
# <a name="coleobjectfactory-class"></a>COleObjectFactory 类

实现 OLE 类工厂，此工厂创建服务器、自动化对象和文档等 OLE 对象。

## <a name="syntax"></a>语法

```
class COleObjectFactory : public CCmdTarget
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COleObject 工厂：COleObject 工厂](#coleobjectfactory)|构造 `COleObjectFactory` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleObject 工厂：获取 ClassID](#getclassid)|返回此工厂创建的对象的 OLE 类 ID。|
|[COleObject 工厂：：许可证有效](#islicensevalid)|确定控件的许可证是否有效。|
|[COleObject 工厂：已注册](#isregistered)|指示对象工厂是否已在 OLE 系统 DLL 中注册。|
|[COleObject 工厂：：注册](#register)|将此对象工厂注册到 OLE 系统 DLL。|
|[COleObject 工厂：：注册所有](#registerall)|使用 OLE 系统 DLL 注册应用程序的所有对象工厂。|
|[COleObject 工厂：撤销](#revoke)|撤消此对象工厂在 OLE 系统 DLL 中的注册。|
|[COleObject 工厂：：撤销所有](#revokeall)|撤销应用程序的对象工厂在 OLE 系统 DLL 中的注册。|
|[COleObject 工厂：：取消注册所有](#unregisterall)|取消注册应用程序的所有对象工厂。|
|[COleObject 工厂：：更新注册](#updateregistry)|将此对象工厂注册到 OLE 系统注册表。|
|[COleObject 工厂：：更新注册所有](#updateregistryall)|使用 OLE 系统注册表注册应用程序的所有对象工厂。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[COleObject 工厂：获取许可密钥](#getlicensekey)|从控件的 DLL 请求唯一的密钥。|
|[COleObject 工厂：：在创建对象上](#oncreateobject)|由框架调用以创建此工厂类型的新对象。|
|[COleObject 工厂：：验证许可密钥](#verifylicensekey)|验证控件中嵌入的密钥是否与容器中嵌入的密钥匹配。|
|[COleObject 工厂：：验证用户许可证](#verifyuserlicense)|验证该控件是否获得设计时使用许可。|

## <a name="remarks"></a>备注

类`COleObjectFactory`具有用于执行以下函数的成员函数：

- 管理对象的注册。

- 更新 OLE 系统寄存器，以及通知 OLE 对象正在运行并准备接收消息的运行时注册。

- 通过在设计时将控件的使用限制为许可开发人员，并在运行时将许可应用程序限制在许可应用程序，从而强制执行许可。

- 使用 OLE 系统注册表注册控制对象工厂。

有关对象创建的详细信息，请参阅["数据对象和数据源 （OLE）"](../../mfc/data-objects-and-data-sources-ole.md)以及[数据对象和数据源：创建和销毁](../../mfc/data-objects-and-data-sources-creation-and-destruction.md)"的文章。 有关注册的更多，[请参阅注册一](../../mfc/registration.md)文。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleObjectFactory`

## <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="coleobjectfactorycoleobjectfactory"></a><a name="coleobjectfactory"></a>COleObject 工厂：COleObject 工厂

构造对象`COleObjectFactory`，将其初始化为未注册的对象工厂，并将其添加到工厂列表中。

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

*Clsid*<br/>
此对象工厂表示的 OLE 类 ID 的引用。

*pRuntime 类*<br/>
指向此工厂可以创建的C++对象的运行时类的指针。

*b 多实例*<br/>
指示应用程序的单个实例是否可以支持多个实例。 如果为 TRUE，则为每个请求启动应用程序的多个实例以创建对象。

*nFlags*<br/>
包含以下一个或多个标志：

- `afxRegDefault`将线程模型设置为线程模型=公寓。

- `afxRegInsertable`允许控件显示在 OLE**对象的"插入对象**"对话框中。

- `afxRegApartmentThreading`将注册表中的线程模型设置为线程模型_公寓。

- `afxRegFreeThreading`将注册表中的线程模型设置为线程模型_自由。

   可以组合两个标志`afxRegApartmentThreading`并`afxRegFreeThreading`设置线程模型_两者。 有关线程模型注册的详细信息，请参阅 Windows SDK 中的[InprocServer32。](/windows/win32/com/inprocserver32)

*lpszProgID*<br/>
指向包含口头程序标识符（如"Microsoft Excel"）的字符串的指针。

### <a name="remarks"></a>备注

但是，要使用该对象，必须注册它。

有关详细信息，请参阅 Windows SDK 中的[CLSID 密钥](/windows/win32/com/clsid-key-hklm)。

## <a name="coleobjectfactorygetclassid"></a><a name="getclassid"></a>COleObject 工厂：获取 ClassID

返回对本工厂表示的 OLE 类 ID 的引用。

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>返回值

引用此工厂表示的 OLE 类 ID。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[CLSID 密钥](/windows/win32/com/clsid-key-hklm)。

## <a name="coleobjectfactorygetlicensekey"></a><a name="getlicensekey"></a>COleObject 工厂：获取许可密钥

从控件的 DLL 请求唯一的许可证密钥，并将其存储在*pbstrKey*指向的 BSTR 中。

```
virtual BOOL GetLicenseKey(
    DWORD dwReserved,
    BSTR* pbstrKey);
```

### <a name="parameters"></a>参数

*dw保留*<br/>
保留供将来使用。

*pbstrKey*<br/>
指向将存储许可证密钥的 BSTR 的指针。

### <a name="return-value"></a>返回值

如果许可证密钥字符串不是 NULL，则非零;否则 0。

### <a name="remarks"></a>备注

此函数的默认实现返回 0，并且不存储在 BSTR 中。 如果使用 MFC ActiveX ControlWizard 创建项目，ControlWizard 会提供检索控件许可证密钥的重写。

## <a name="coleobjectfactoryislicensevalid"></a><a name="islicensevalid"></a>COleObject 工厂：：许可证有效

确定控件的许可证是否有效。

```
BOOL IsLicenseValid();
```

### <a name="return-value"></a>返回值

如果成功，就是真实的;否则是虚假的。

## <a name="coleobjectfactoryisregistered"></a><a name="isregistered"></a>COleObject 工厂：已注册

如果工厂在 OLE 系统 DLL 中注册，则返回非零值。

```
virtual BOOL IsRegistered() const;
```

### <a name="return-value"></a>返回值

如果工厂已注册，则非零;否则 0。

## <a name="coleobjectfactoryoncreateobject"></a><a name="oncreateobject"></a>COleObject 工厂：：在创建对象上

由框架调用以创建新对象。

```
virtual CCmdTarget* OnCreateObject();
```

### <a name="return-value"></a>返回值

指向创建对象的指针。 如果失败，可能会引发内存异常。

### <a name="remarks"></a>备注

重写此函数，以便从传递给构造函数的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)以外的内容创建对象。

## <a name="coleobjectfactoryregister"></a><a name="register"></a>COleObject 工厂：：注册

将此对象工厂注册到 OLE 系统 DLL。

```
virtual BOOL Register();
```

### <a name="return-value"></a>返回值

如果工厂已成功注册，则非零;否则 0。

### <a name="remarks"></a>备注

此函数通常由[CWinApp：：在](../../mfc/reference/cwinapp-class.md#initinstance)应用程序启动时调用 IninInstance。

## <a name="coleobjectfactoryregisterall"></a><a name="registerall"></a>COleObject 工厂：：注册所有

使用 OLE 系统 DLL 注册应用程序的所有对象工厂。

```
static BOOL PASCAL RegisterAll();
```

### <a name="return-value"></a>返回值

如果工厂成功注册，则非零;否则 0。

### <a name="remarks"></a>备注

此函数通常由[CWinApp：：在](../../mfc/reference/cwinapp-class.md#initinstance)应用程序启动时调用 IninInstance。

## <a name="coleobjectfactoryrevoke"></a><a name="revoke"></a>COleObject 工厂：撤销

撤消此对象工厂在 OLE 系统 DLL 中的注册。

```
void Revoke();
```

### <a name="remarks"></a>备注

框架在应用程序终止之前自动调用此函数。 如有必要，请从[CWinApp：：ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)的重写调用它。

## <a name="coleobjectfactoryrevokeall"></a><a name="revokeall"></a>COleObject 工厂：：撤销所有

撤销应用程序在 OLE 系统 DLL 上的所有对象工厂的注册。

```
static void PASCAL RevokeAll();
```

### <a name="remarks"></a>备注

框架在应用程序终止之前自动调用此函数。 如有必要，请从[CWinApp：：ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)的重写调用它。

## <a name="coleobjectfactoryunregisterall"></a><a name="unregisterall"></a>COleObject 工厂：：取消注册所有

取消注册应用程序的所有对象工厂。

```
static BOOL PASCAL UnregisterAll();
```

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

## <a name="coleobjectfactoryupdateregistry"></a><a name="updateregistry"></a>COleObject 工厂：：更新注册

使用 OLE 系统注册表注册应用程序的所有对象工厂。

```
void UpdateRegistry(LPCTSTR lpszProgID = NULL);
virtual BOOL UpdateRegistry(BOOL bRegister);
```

### <a name="parameters"></a>参数

*lpszProgID*<br/>
指向包含人可读程序标识符（如"Excel.Document.5"）的字符串的指针。

*b 注册*<br/>
确定是否应注册控件类的对象工厂。

### <a name="remarks"></a>备注

此函数的两种形式的简要讨论如下：

- **更新注册处）** `lpszProgID` **)** 将此对象工厂注册到 OLE 系统注册表。 此函数通常由[CWinApp：：在](../../mfc/reference/cwinapp-class.md#initinstance)应用程序启动时调用 IninInstance。

- **更新注册处）** `bRegister` **)** 函数的这种形式是可重写的。 如果*b寄存器*为 TRUE，则此函数将控制类注册到系统注册表中。 否则，它将取消注册类。

   如果使用 MFC ActiveX ControlWizard 创建项目，ControlWizard 会为此纯虚拟函数提供覆盖。

## <a name="coleobjectfactoryupdateregistryall"></a><a name="updateregistryall"></a>COleObject 工厂：：更新注册所有

使用 OLE 系统注册表注册应用程序的所有对象工厂。

```
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```

### <a name="parameters"></a>参数

*b 注册*<br/>
确定是否应注册控件类的对象工厂。

### <a name="return-value"></a>返回值

如果成功更新工厂，则非零;否则 0。

### <a name="remarks"></a>备注

此函数通常由[CWinApp：：在](../../mfc/reference/cwinapp-class.md#initinstance)应用程序启动时调用 IninInstance。

## <a name="coleobjectfactoryverifylicensekey"></a><a name="verifylicensekey"></a>COleObject 工厂：：验证许可密钥

验证容器是否被许可使用 OLE 控件。

```
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```

### <a name="parameters"></a>参数

*bstrKey*<br/>
存储容器版本的许可证字符串的 BSTR。

### <a name="return-value"></a>返回值

如果运行时许可证有效，则非零;否则 0。

### <a name="remarks"></a>备注

默认版本调用[GetLicenseKey](#getlicensekey)获取控件的许可证字符串的副本，并将其与*bstrKey*中的字符串进行比较。 如果两个字符串匹配，则函数返回一个非零值;如果两个字符串匹配，则函数将返回一个非零值。否则它返回 0。

您可以重写此函数以提供许可证的自定义验证。

功能[验证用户许可证](#verifyuserlicense)验证设计时许可证。

## <a name="coleobjectfactoryverifyuserlicense"></a><a name="verifyuserlicense"></a>COleObject 工厂：：验证用户许可证

验证 OLE 控件的设计时许可证。

```
virtual BOOL VerifyUserLicense();
```

### <a name="return-value"></a>返回值

如果设计时许可证有效，则非零;否则 0。

## <a name="see-also"></a>另请参阅

[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleTemplateServer 类](../../mfc/reference/coletemplateserver-class.md)
