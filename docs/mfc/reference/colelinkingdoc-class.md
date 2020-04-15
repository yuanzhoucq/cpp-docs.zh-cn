---
title: COle链接文档类
ms.date: 11/04/2016
f1_keywords:
- COleLinkingDoc
- AFXOLE/COleLinkingDoc
- AFXOLE/COleLinkingDoc::COleLinkingDoc
- AFXOLE/COleLinkingDoc::Register
- AFXOLE/COleLinkingDoc::Revoke
- AFXOLE/COleLinkingDoc::OnFindEmbeddedItem
- AFXOLE/COleLinkingDoc::OnGetLinkedItem
helpviewer_keywords:
- COleLinkingDoc [MFC], COleLinkingDoc
- COleLinkingDoc [MFC], Register
- COleLinkingDoc [MFC], Revoke
- COleLinkingDoc [MFC], OnFindEmbeddedItem
- COleLinkingDoc [MFC], OnGetLinkedItem
ms.assetid: 9f547f35-2f95-427f-b9c0-85c31940198b
ms.openlocfilehash: f9f184542aaceb206d3eae110d3a088d5fbc95cf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374943"
---
# <a name="colelinkingdoc-class"></a>COle链接文档类

支持链接到所包含的嵌入项的 OLE 容器文档的基类。

## <a name="syntax"></a>语法

```
class COleLinkingDoc : public COleDocument
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COle链接文档：：COle链接文档](#colelinkingdoc)|构造 `COleLinkingDoc` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COle链接文档：：注册](#register)|将文档注册到 OLE 系统 DLL。|
|[COle链接文档：撤销](#revoke)|撤销文档的注册。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[COle链接文档：：在查找嵌入式项目](#onfindembeddeditem)|查找指定的嵌入项。|
|[COlelinkDoc：：上链接项目](#ongetlinkeditem)|查找指定的链接项。|

## <a name="remarks"></a>备注

支持链接到嵌入项的容器应用程序称为"链接容器"。 [OCLIENT](../../overview/visual-cpp-samples.md)示例应用程序是链接容器的示例。

当链接项的源是另一个文档中的嵌入项时，必须加载包含文档才能编辑嵌入项。 因此，当用户想要编辑链接项的源时，链接容器必须能够由另一个容器应用程序启动。 您的应用程序还必须使用[COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)类，以便在以编程方式启动时创建文档。

要使容器成为链接容器，请从`COleLinkingDoc`[COleDocument](../../mfc/reference/coledocument-class.md)派生文档类。 与任何其他 OLE 容器一样，必须设计用于存储应用程序的本机数据以及嵌入或链接项的类。 此外，还必须设计用于存储本机数据的数据结构。 如果为应用程序的本机`CDocItem`数据定义派生类，则可以使用 定义的`COleDocument`接口来存储本机数据和 OLE 数据。

要允许应用程序由另一个容器以编程方式启动，请声明`COleTemplateServer`对象为应用程序`CWinApp`派生类的成员：

[!code-cpp[NVC_MFCOleContainer#23](../../mfc/codesnippet/cpp/colelinkingdoc-class_1.h)]

在`InitInstance``CWinApp`派生类的成员函数中，创建文档模板并将`COleLinkingDoc`派生类指定为文档类：

[!code-cpp[NVC_MFCOleContainer#24](../../mfc/codesnippet/cpp/colelinkingdoc-class_2.cpp)]

通过调用`COleTemplateServer`对象`ConnectTemplate`的成员函数将对象连接到文档模板，并通过调用`COleTemplateServer::RegisterAll`：

[!code-cpp[NVC_MFCOleContainer#25](../../mfc/codesnippet/cpp/colelinkingdoc-class_3.cpp)]

有关示例`CWinApp`派生类定义和`InitInstance`函数，请参阅 OCLIENT。H 和 OCLIENT。MFC 样本[OCLIENT](../../overview/visual-cpp-samples.md)中的 CPP。

有关使用`COleLinkingDoc`的详细信息，请参阅[文章容器：实现容器](../../mfc/containers-implementing-a-container.md)和[容器：高级功能](../../mfc/containers-advanced-features.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

`COleLinkingDoc`

## <a name="requirements"></a>要求

**标题：** afxole.h

## <a name="colelinkingdoccolelinkingdoc"></a><a name="colelinkingdoc"></a>COle链接文档：：COle链接文档

构造`COleLinkingDoc`对象而不开始与 OLE 系统 DLL 通信。

```
COleLinkingDoc();
```

### <a name="remarks"></a>备注

您必须调用`Register`成员函数，通知 OLE 文档已打开。

## <a name="colelinkingdoconfindembeddeditem"></a><a name="onfindembeddeditem"></a>COle链接文档：：在查找嵌入式项目

由框架调用以确定文档是否包含具有指定名称的嵌入式 OLE 项。

```
virtual COleClientItem* OnFindEmbeddedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>参数

*lpszItem名称*<br/>
指向请求的嵌入 OLE 项的名称。

### <a name="return-value"></a>返回值

指向指定项的指针;指向指定项的指针。如果未找到该项目，则为 NULL。

### <a name="remarks"></a>备注

默认实现搜索具有指定名称的项的嵌入项列表（名称比较区分大小写）。 如果您有自己的方法来存储或命名嵌入的 OLE 项，请重写此函数。

## <a name="colelinkingdocongetlinkeditem"></a><a name="ongetlinkeditem"></a>COlelinkDoc：：上链接项目

由框架调用以检查文档是否包含具有指定名称的链接服务器项。

```
virtual COleServerItem* OnGetLinkedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>参数

*lpszItem名称*<br/>
指向请求的链接 OLE 项的名称。

### <a name="return-value"></a>返回值

指向指定项的指针;指向指定项的指针。如果未找到该项目，则为 NULL。

### <a name="remarks"></a>备注

默认`COleLinkingDoc`实现始终返回 NULL。 此函数在派生类`COleServerDoc`中重写，以搜索具有指定名称的链接项的 OLE 服务器项列表（名称比较区分大小写）。 如果您已经实现了自己的存储或检索链接的服务器项的方法，请重写此函数。

## <a name="colelinkingdocregister"></a><a name="register"></a>COle链接文档：：注册

通知 OLE 系统 DLL 文档已打开。

```
BOOL Register(
    COleObjectFactory* pFactory,
    LPCTSTR lpszPathName);
```

### <a name="parameters"></a>参数

*pFactory*<br/>
指向 OLE 工厂对象的指针（可以是 NULL）。

*lpszPath名称*<br/>
指向容器文档完全限定路径的指针。

### <a name="return-value"></a>返回值

如果文档已成功注册，则非零;否则 0。

### <a name="remarks"></a>备注

创建或打开命名文件以将文档注册到 OLE 系统 DLL 时调用此功能。 如果文档表示嵌入的项，则无需调用此函数。

如果在应用程序中使用`COleTemplateServer`，`Register`则 由`COleLinkingDoc`的 实现`OnNewDocument`调用 。 `OnSaveDocument` `OnOpenDocument`

## <a name="colelinkingdocrevoke"></a><a name="revoke"></a>COle链接文档：撤销

通知 OLE 系统 DLL 文档不再打开。

```
void Revoke();
```

### <a name="remarks"></a>备注

调用此函数以撤销文档在 OLE 系统 DLL 中的注册。

关闭命名文件时应调用此函数，但通常不需要直接调用它。 `Revoke`是`COleLinkingDoc`按 的`OnCloseDocument`实现来调用 的`OnNewDocument`，`OnOpenDocument`和`OnSaveDocument`。

## <a name="see-also"></a>另请参阅

[MFC 样品 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDocument 类](../../mfc/reference/coledocument-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)
