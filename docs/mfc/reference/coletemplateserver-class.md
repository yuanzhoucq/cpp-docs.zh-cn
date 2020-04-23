---
title: COleTemplateServer 类
ms.date: 11/04/2016
f1_keywords:
- COleTemplateServer
- AFXDISP/COleTemplateServer
- AFXDISP/COleTemplateServer::COleTemplateServer
- AFXDISP/COleTemplateServer::ConnectTemplate
- AFXDISP/COleTemplateServer::Unregister
- AFXDISP/COleTemplateServer::UpdateRegistry
helpviewer_keywords:
- COleTemplateServer [MFC], COleTemplateServer
- COleTemplateServer [MFC], ConnectTemplate
- COleTemplateServer [MFC], Unregister
- COleTemplateServer [MFC], UpdateRegistry
ms.assetid: 47a2887d-8162-4993-a842-a784177c7f5c
ms.openlocfilehash: 561da5060aae3c938dc3e55d0310718a881c1a3b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753728"
---
# <a name="coletemplateserver-class"></a>COleTemplateServer 类

用于 OLE 可视编辑服务器、自动化服务器和链接容器（支持链接到嵌入的应用程序）。

## <a name="syntax"></a>语法

```
class COleTemplateServer : public COleObjectFactory
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COle模板服务器：COleTemplate服务器](#coletemplateserver)|构造 `COleTemplateServer` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleTemplate服务器：连接模板](#connecttemplate)|将文档模板连接到基础`COleObjectFactory`对象。|
|[COleTemplate服务器：取消注册](#unregister)|取消注册关联的文档模板。|
|[COleTemplate服务器：更新注册](#updateregistry)|将文档类型注册到 OLE 系统注册表。|

## <a name="remarks"></a>备注

此类派生自类[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md);通常，您可以直接使用`COleTemplateServer`，而不是派生您自己的类。 `COleTemplateServer`使用[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)对象管理服务器文档。 在实现`COleTemplateServer`完整服务器时使用，即可作为独立应用程序运行的服务器。 尽管支持单一文档接口 （SDI） 应用程序，但完整服务器通常是多个文档接口 （MDI） 应用程序。 对于`COleTemplateServer`应用程序支持的每种类型的服务器文档，需要一个对象;也就是说，如果服务器应用程序同时支持工作表和图表，则必须有两`COleTemplateServer`个对象。

`COleTemplateServer`覆盖 由`OnCreateInstance``COleObjectFactory`定义的成员函数。 框架调用此成员函数以创建正确类型的C++对象。

有关服务器的详细信息，请参阅文章["服务器：实现服务器](../../mfc/servers-implementing-a-server.md)"。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleObject工厂](../../mfc/reference/coleobjectfactory-class.md)

`COleTemplateServer`

## <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="coletemplateservercoletemplateserver"></a><a name="coletemplateserver"></a>COle模板服务器：COleTemplate服务器

构造 `COleTemplateServer` 对象。

```
COleTemplateServer();
```

### <a name="remarks"></a>备注

有关类使用情况的简要说明，`COleTemplateServer`请参阅[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)类概述。

## <a name="coletemplateserverconnecttemplate"></a><a name="connecttemplate"></a>COleTemplate服务器：连接模板

将*pDocTemplate*指向的文档模板连接到基础的[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)对象。

```cpp
void ConnectTemplate(
    REFCLSID clsid,
    CDocTemplate* pDocTemplate,
    BOOL bMultiInstance);
```

### <a name="parameters"></a>参数

*Clsid*<br/>
引用模板请求的 OLE 类 ID。

*pDocTemplate*<br/>
指向文档模板的指针。

*b 多实例*<br/>
指示应用程序的单个实例是否可以支持多个实例。 如果为 TRUE，则为每个请求启动应用程序的多个实例以创建对象。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[CLSID 密钥](/windows/win32/com/clsid-key-hklm)。

## <a name="coletemplateserverunregister"></a><a name="unregister"></a>COleTemplate服务器：取消注册

取消注册关联的文档模板。

```
BOOL Unregister();
```

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

输入注释

## <a name="coletemplateserverupdateregistry"></a><a name="updateregistry"></a>COleTemplate服务器：更新注册

从文档模板字符串加载文件类型信息，并将该信息放在 OLE 系统注册表中。

```cpp
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL,
    BOOL bRegister = TRUE);
```

### <a name="parameters"></a>参数

*nAppType*<br/>
OLE_APPTYPE枚举中的值，在 AFXDISP 中定义。H。 它可以具有以下任一值：

- OAT_INPLACE_SERVER服务器具有完整的服务器用户界面。

- OAT_SERVER服务器仅支持嵌入。

- OAT_CONTAINER容器支持指向嵌入对象的链接。

- OAT_DISPATCH_OBJECT 对象`IDispatch`是 - 支持。

- OAT_DOC_OBJECT_SERVER服务器支持嵌入和文档对象组件模型。

*rglpsz注册*<br/>
仅当不存在条目时，才写入注册表的条目的列表。

*rglpsz 覆盖*<br/>
写入注册表的条目列表，而不考虑是否存在任何前面的条目。

*b 注册*<br/>
确定是否应注册类。 如果*b寄存器*为 TRUE，则类将注册到系统注册表。 否则，它将取消注册类。

### <a name="remarks"></a>备注

注册信息通过调用[CDocTemplate 加载：GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)。 检索的子字符串是索引标识的子字符串`regFileTypeId`，`regFileTypeName`和`fileNewName`，如`GetDocString`参考页中所述。

如果`regFileTypeId`子字符串为空，或者调用`GetDocString`失败的原因为任何其他原因，则此函数将失败，并且未在注册表中输入文件信息。

参数*rglpsz 注册*和*rglpszOverwrite*中的信息通过调用[AfxOleRegisterServerServerClass](application-control.md#afxoleregisterserverclass)写入注册表。 默认信息在两个参数为 NULL 时注册，适用于大多数应用程序。 有关这些参数中信息的结构的信息，请参阅`AfxOleRegisterServerClass`。

有关详细信息，请参阅 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

## <a name="see-also"></a>请参阅

[MFC 样品 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleObjectFactory 类](../../mfc/reference/coleobjectfactory-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc 类](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleServer 项目类](../../mfc/reference/coleserveritem-class.md)
