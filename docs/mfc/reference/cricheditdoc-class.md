---
title: CRichEditDoc 类
ms.date: 11/04/2016
f1_keywords:
- CRichEditDoc
- AFXRICH/CRichEditDoc
- AFXRICH/CRichEditDoc::CreateClientItem
- AFXRICH/CRichEditDoc::GetStreamFormat
- AFXRICH/CRichEditDoc::GetView
- AFXRICH/CRichEditDoc::m_bRTF
helpviewer_keywords:
- CRichEditDoc [MFC], CreateClientItem
- CRichEditDoc [MFC], GetStreamFormat
- CRichEditDoc [MFC], GetView
- CRichEditDoc [MFC], m_bRTF
ms.assetid: c936ec18-d516-49d4-b7fb-c9aa0229eddc
ms.openlocfilehash: 587cf65543e24e586fb8b2336481d6e841473134
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368263"
---
# <a name="cricheditdoc-class"></a>CRichEditDoc 类

使用[CRichEditView](../../mfc/reference/cricheditview-class.md)和[CRichEditCntrItem，](../../mfc/reference/cricheditcntritem-class.md)在 MFC 的文档视图体系结构上下文中提供了丰富的编辑控件的功能。

## <a name="syntax"></a>语法

```
class CRichEditDoc : public COleServerDoc
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[克里希编辑文档：创建客户端项目](#createclientitem)|调用 以执行文档的清理。|
|[克里希编辑文档：获取流格式](#getstreamformat)|指示流输入和输出是否应包含格式设置信息。|
|[克里希编辑文档：获取视图](#getview)|检索同化[CRichEditView](../../mfc/reference/cricheditview-class.md)对象。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[克里希编辑文档：m_bRTF](#m_brtf)|指示流 I/O 是否应包含格式。|

## <a name="remarks"></a>备注

"富编辑控件"是用户可以在其中输入和编辑文本的窗口。 文本可以分配字符和段落格式，并可以包括嵌入的 OLE 对象。 丰富的编辑控件为文本格式设置提供了编程界面。 但是，应用程序必须实现使用户可进行格式设置操作所需的任何用户界面组件。

`CRichEditView` 保留文本及其格式特征。 `CRichEditDoc`维护视图中的客户端项的列表。 `CRichEditCntrItem`提供对 OLE 客户端项的容器端访问。

此 Windows 通用控件（因此[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相关类）仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 及更高版本下运行的程序。

有关在 MFC 应用程序中使用富编辑文档的示例，请参阅[WORDPAD](../../overview/visual-cpp-samples.md)示例应用程序。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)

`CRichEditDoc`

## <a name="requirements"></a>要求

**标题：** afxrich.h

## <a name="cricheditdoccreateclientitem"></a><a name="createclientitem"></a>克里希编辑文档：创建客户端项目

调用此函数以创建对象`CRichEditCntrItem`并将其添加到此文档。

```
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;
```

### <a name="parameters"></a>参数

*普雷奥*<br/>
指向描述 OLE 项的[REOBJECT](/windows/win32/api/richole/ns-richole-reobject)结构的指针。 新`CRichEditCntrItem`对象围绕此 OLE 项构造。 如果*Preo*为 NULL，则新客户端项为空。

### <a name="return-value"></a>返回值

指向已添加到本文档的新[CRichEditCntrItem 对象](../../mfc/reference/cricheditcntritem-class.md)。

### <a name="remarks"></a>备注

此功能不执行任何 OLE 初始化。

有关详细信息，请参阅 Windows SDK 中的[REOBJECT](/windows/win32/api/richole/ns-richole-reobject)结构。

## <a name="cricheditdocgetstreamformat"></a><a name="getstreamformat"></a>克里希编辑文档：获取流格式

调用此函数以确定流丰富的编辑内容的文本格式。

```
int GetStreamFormat() const;
```

### <a name="return-value"></a>返回值

以下标志之一：

- SF_TEXT 指示富编辑控件不维护格式设置信息。

- SF_RTF 指示富编辑控件确实维护格式信息。

### <a name="remarks"></a>备注

返回值基于[m_bRTF](#m_brtf)数据成员。 如果`m_bRTF`为 TRUE，则此函数将返回SF_RTF;否则，SF_TEXT。

## <a name="cricheditdocgetview"></a><a name="getview"></a>克里希编辑文档：获取视图

调用此函数以访问与此`CRichEditDoc`对象关联的[CRichEditView](../../mfc/reference/cricheditview-class.md)对象。

```
virtual CRichEditView* GetView() const;
```

### <a name="return-value"></a>返回值

指向与文档`CRichEditView`关联的对象的指针。

### <a name="remarks"></a>备注

文本和格式信息包含在对象中`CRichEditView`。 对象`CRichEditDoc`维护用于序列化的 OLE 项。 每个`CRichEditDoc`应该只有一个`CRichEditView`。

## <a name="cricheditdocm_brtf"></a><a name="m_brtf"></a>克里希编辑文档：m_bRTF

当 TRUE 时，指示[CRichEditCtrl：：StreamIn](../../mfc/reference/cricheditctrl-class.md#streamin)和[CRichEditCtrl：：Streamout](../../mfc/reference/cricheditctrl-class.md#streamout)应存储段落和字符格式特征。

```
BOOL m_bRTF;
```

## <a name="see-also"></a>另请参阅

[MFC 样品 WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[COleServerDoc 类](../../mfc/reference/coleserverdoc-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[克里希编辑视图类](../../mfc/reference/cricheditview-class.md)<br/>
[CRichEditCntrItem 类](../../mfc/reference/cricheditcntritem-class.md)<br/>
[COleDocument 类](../../mfc/reference/coledocument-class.md)<br/>
[CRichEditCtrl 类](../../mfc/reference/cricheditctrl-class.md)
