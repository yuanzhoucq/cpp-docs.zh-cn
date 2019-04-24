---
title: COleLinkingDoc 类
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
ms.openlocfilehash: c5076ceef0c6626fac0232fadf6818edd78b4ccf
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58773549"
---
# <a name="colelinkingdoc-class"></a>COleLinkingDoc 类

支持链接到所包含的嵌入项的 OLE 容器文档的基类。

## <a name="syntax"></a>语法

```
class COleLinkingDoc : public COleDocument
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleLinkingDoc::COleLinkingDoc](#colelinkingdoc)|构造 `COleLinkingDoc` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleLinkingDoc::Register](#register)|使用 OLE 系统 Dll 注册文档。|
|[COleLinkingDoc::Revoke](#revoke)|撤消文档的注册。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[COleLinkingDoc::OnFindEmbeddedItem](#onfindembeddeditem)|查找指定的嵌入的项。|
|[COleLinkingDoc::OnGetLinkedItem](#ongetlinkeditem)|查找指定的链接的项。|

## <a name="remarks"></a>备注

支持将链接到嵌入的项的容器应用程序称为"链接容器"。 [OCLIENT](../../overview/visual-cpp-samples.md)示例应用程序是链接容器的示例。

链接的项的源是在另一个文档，必须在要编辑嵌入项的顺序加载包含文档中嵌入的项。 出于此原因，链接容器必须能够在用户想要编辑的链接项目源时由另一个容器应用程序启动。 你的应用程序还必须使用[COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)类，以便它可以创建文档时以编程方式启动。

若要使容器链接容器，派生文档类从`COleLinkingDoc`而不是[COleDocument](../../mfc/reference/coledocument-class.md)。 与任何其他 OLE 容器，必须设计你的类用于存储应用程序的本机数据以及嵌入或链接的项。 此外，您必须设计用于将本机数据存储的数据结构。 如果定义了`CDocItem`的派生类，为你的应用程序的本机数据，可以使用所定义接口`COleDocument`本机数据以及 OLE 数据存储。

若要允许应用程序能够以编程方式启动的另一个容器，请声明`COleTemplateServer`对象的应用程序的成员作为`CWinApp`-派生的类：

[!code-cpp[NVC_MFCOleContainer#23](../../mfc/codesnippet/cpp/colelinkingdoc-class_1.h)]

在`InitInstance`成员函数在`CWinApp`-派生的类，创建文档模板，并指定你`COleLinkingDoc`-派生的类作为文档类：

[!code-cpp[NVC_MFCOleContainer#24](../../mfc/codesnippet/cpp/colelinkingdoc-class_2.cpp)]

连接你`COleTemplateServer`到通过调用对象的文档模板对象`ConnectTemplate`成员函数，并注册所有类的都对象与 OLE 系统通过调用`COleTemplateServer::RegisterAll`:

[!code-cpp[NVC_MFCOleContainer#25](../../mfc/codesnippet/cpp/colelinkingdoc-class_3.cpp)]

有关示例`CWinApp`的派生类定义和`InitInstance`函数中，请参阅 OCLIENT。H 和 OCLIENT。在 MFC 示例 CPP [OCLIENT](../../overview/visual-cpp-samples.md)。

有关使用的详细信息`COleLinkingDoc`，请参阅文章[容器：实现容器](../../mfc/containers-implementing-a-container.md)和[容器：高级功能](../../mfc/containers-advanced-features.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

`COleLinkingDoc`

## <a name="requirements"></a>要求

**标头：** afxole.h

##  <a name="colelinkingdoc"></a>  COleLinkingDoc::COleLinkingDoc

构造`COleLinkingDoc`没有从与 OLE 系统 Dll 之间的通信对象。

```
COleLinkingDoc();
```

### <a name="remarks"></a>备注

必须调用`Register`成员函数，以通知 OLE 文档处于打开状态。

##  <a name="onfindembeddeditem"></a>  COleLinkingDoc::OnFindEmbeddedItem

由框架调用以确定文档是否包含具有指定名称的嵌入的 OLE 项。

```
virtual COleClientItem* OnFindEmbeddedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>参数

*lpszItemName*<br/>
指向嵌入 OLE 项请求的名称。

### <a name="return-value"></a>返回值

指向指定的项;如果未找到该项，则为 NULL。

### <a name="remarks"></a>备注

默认实现将搜索具有指定名称 （名称比较不区分大小写） 的项的嵌入项的列表。 如果您有自己的存储或命名嵌入的 OLE 项的方法，重写此函数。

##  <a name="ongetlinkeditem"></a>  COleLinkingDoc::OnGetLinkedItem

由框架调用以检查文档是否包含具有指定名称的链接的服务器项。

```
virtual COleServerItem* OnGetLinkedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>参数

*lpszItemName*<br/>
指向链接 OLE 项请求的名称。

### <a name="return-value"></a>返回值

指向指定的项;如果未找到该项，则为 NULL。

### <a name="remarks"></a>备注

默认值`COleLinkingDoc`实现始终返回 NULL。 此函数是在派生类中的重写`COleServerDoc`搜索具有指定名称 （名称比较不区分大小写） 链接的项的 OLE 服务器项的列表。 如果已实现您自己的存储或检索链接的服务器项的方法，重写此函数。

##  <a name="register"></a>  COleLinkingDoc::Register

告知 OLE 系统 Dll 文档处于打开状态。

```
BOOL Register(
    COleObjectFactory* pFactory,
    LPCTSTR lpszPathName);
```

### <a name="parameters"></a>参数

*pFactory*<br/>
指向 OLE 工厂对象 （可以为 NULL）。

*lpszPathName*<br/>
指向容器文档的完全限定路径。

### <a name="return-value"></a>返回值

如果成功注册文档; 非零值否则为 0。

### <a name="remarks"></a>备注

调用此函数时创建或打开要将文档注册 OLE 系统 Dll 的命名的文件。 没有无需调用此函数，如果文档表示嵌入的项。

如果使用的`COleTemplateServer`应用程序中`Register`为您通过调用`COleLinkingDoc`的实现`OnNewDocument`， `OnOpenDocument`，并`OnSaveDocument`。

##  <a name="revoke"></a>  COleLinkingDoc::Revoke

告知 OLE 系统 Dll 文档不再处于打开状态。

```
void Revoke();
```

### <a name="remarks"></a>备注

调用此函数可撤消向 OLE 系统 Dll 的文档的注册。

关闭的命名的文件时，应调用此函数，但通常不需要直接调用。 `Revoke` 为您通过调用`COleLinkingDoc`的实现`OnCloseDocument`， `OnNewDocument`， `OnOpenDocument`，和`OnSaveDocument`。

## <a name="see-also"></a>请参阅

[MFC 示例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDocument 类](../../mfc/reference/coledocument-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)
