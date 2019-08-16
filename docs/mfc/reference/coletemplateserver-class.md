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
ms.openlocfilehash: 4a1997497f3bddb405b712b5534f76e577dabfa8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503085"
---
# <a name="coletemplateserver-class"></a>COleTemplateServer 类

用于 OLE 可视编辑服务器、自动化服务器和链接容器（支持链接到嵌入的应用程序）。

## <a name="syntax"></a>语法

```
class COleTemplateServer : public COleObjectFactory
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleTemplateServer::COleTemplateServer](#coletemplateserver)|构造 `COleTemplateServer` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleTemplateServer::ConnectTemplate](#connecttemplate)|将文档模板连接到基础`COleObjectFactory`对象。|
|[COleTemplateServer::Unregister](#unregister)|注销关联的文档模板。|
|[COleTemplateServer::UpdateRegistry](#updateregistry)|向 OLE 系统注册表注册文档类型。|

## <a name="remarks"></a>备注

此类派生自类[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md);通常, 你可以直接`COleTemplateServer`使用, 而不是派生你自己的类。 `COleTemplateServer`使用[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)对象管理服务器文档。 实现`COleTemplateServer`完整服务器时使用, 即可以作为独立应用程序运行的服务器。 尽管支持单文档界面 (SDI) 应用程序, 但完整服务器通常是多文档界面 (MDI) 应用程序。 应用`COleTemplateServer`程序支持的每种服务器文档都需要一个对象; 也就是说, 如果你的服务器应用程序同时支持工作表和图表, 则必须具有`COleTemplateServer`两个对象。

`COleTemplateServer`重写`OnCreateInstance`由`COleObjectFactory`定义的成员函数。 框架调用此成员函数以创建适当类型的C++对象。

有关服务器的详细信息, 请参阅文章[服务器:实现服务器](../../mfc/servers-implementing-a-server.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)

`COleTemplateServer`

## <a name="requirements"></a>要求

**标头：** afxdisp.h

##  <a name="coletemplateserver"></a>COleTemplateServer:: COleTemplateServer

构造 `COleTemplateServer` 对象。

```
COleTemplateServer();
```

### <a name="remarks"></a>备注

有关`COleTemplateServer`类使用的简短说明, 请参阅[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)类概述。

##  <a name="connecttemplate"></a>  COleTemplateServer::ConnectTemplate

将*pDocTemplate*指向的文档模板连接到基础[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)对象。

```
void ConnectTemplate(
    REFCLSID clsid,
    CDocTemplate* pDocTemplate,
    BOOL bMultiInstance);
```

### <a name="parameters"></a>参数

*clsid*<br/>
对模板所请求的 OLE 类 ID 的引用。

*pDocTemplate*<br/>
指向文档模板的指针。

*bMultiInstance*<br/>
指示应用程序的单个实例是否可以支持多个实例化。 如果为 TRUE, 则为每个请求启动应用程序的多个实例, 以创建对象。

### <a name="remarks"></a>备注

有关详细信息, 请参阅 Windows SDK 中的[CLSID 关键字](/windows/win32/com/clsid-key-hklm)。

##  <a name="unregister"></a>  COleTemplateServer::Unregister

注销关联的文档模板。

```
BOOL Unregister();
```

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

EnterRemarks

##  <a name="updateregistry"></a>COleTemplateServer:: UpdateRegistry

从文档模板字符串加载文件类型信息, 并将该信息放在 OLE 系统注册表中。

```
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL,
    BOOL bRegister = TRUE);
```

### <a name="parameters"></a>参数

*nAppType*<br/>
OLE_APPTYPE 枚举中的一个值, 该值在 AFXDISP.H&AMP;GT 中定义。高. 它可以具有下列值之一:

- OAT_INPLACE_SERVER 服务器具有完全服务器用户界面。

- OAT_SERVER 服务器仅支持嵌入。

- OAT_CONTAINER 容器支持指向嵌入对象的链接。

- OAT_DISPATCH_OBJECT 对象`IDispatch`支持。

- OAT_DOC_OBJECT_SERVER Server 支持嵌入和文档对象组件模型。

*rglpszRegister*<br/>
仅当不存在任何项时才写入注册表的项的列表。

*rglpszOverwrite*<br/>
写入注册表中的项的列表, 不管前面的任何项是否存在。

*bRegister*<br/>
确定是否要注册该类。 如果*bRegister*为 TRUE, 则向系统注册表注册该类。 否则, 将取消注册类。

### <a name="remarks"></a>备注

注册信息通过调用[CDocTemplate:: GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)来加载。 检索到的子字符串由`regFileTypeId`索引、 `regFileTypeName`和`fileNewName`标识, 如`GetDocString`参考页中所述。

如果子字符串为空或由于任何其他原因`GetDocString`而导致对的调用失败, 则此函数将失败, 并且不会在注册表中输入文件信息。 `regFileTypeId`

参数*rglpszRegister*和*rglpszOverwrite*中的信息通过调用[AfxOleRegisterServerClass](application-control.md#afxoleregisterserverclass)写入注册表。 在两个参数为 NULL 时注册的默认信息适用于大多数应用程序。 有关这些参数中信息的结构的信息, 请参阅`AfxOleRegisterServerClass`。

有关更多信息，请参见 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

## <a name="see-also"></a>请参阅

[MFC 示例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleObjectFactory 类](../../mfc/reference/coleobjectfactory-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc 类](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleServerItem 类](../../mfc/reference/coleserveritem-class.md)
