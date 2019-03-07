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
ms.openlocfilehash: 4c2021128dcc06a76cf3b68c0ec49b72a5860046
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295131"
---
# <a name="cricheditdoc-class"></a>CRichEditDoc 类

与[CRichEditView](../../mfc/reference/cricheditview-class.md)并[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)，提供 MFC 文档视图体系结构的上下文中 rich edit 控件的功能。

## <a name="syntax"></a>语法

```
class CRichEditDoc : public COleServerDoc
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CRichEditDoc::CreateClientItem](#createclientitem)|调用以执行清理的文档。|
|[CRichEditDoc::GetStreamFormat](#getstreamformat)|指示流输入和输出是否应包含格式设置信息。|
|[CRichEditDoc::GetView](#getview)|检索关联[CRichEditView](../../mfc/reference/cricheditview-class.md)对象。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CRichEditDoc::m_bRTF](#m_brtf)|指示流 I/O 是否应包含格式设置。|

## <a name="remarks"></a>备注

"格式文本编辑控件"是一个窗口，用户可以输入和编辑文本。 文本字符和段落格式设置，可以分配，并且可以包含嵌入的 OLE 对象。 Rich edit 控件提供用于设置文本格式的编程接口。 但是，应用程序必须实现使用户可进行格式设置操作所需的任何用户界面组件。

`CRichEditView` 保留文本及其格式特征。 `CRichEditDoc` 维护视图中的客户端项目的列表。 `CRichEditCntrItem` 提供对 OLE 客户端项的容器端访问。

此 Windows 公共控件 (并因此[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相关类) 仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 下运行的程序和更高版本。

在 MFC 应用程序中使用格式文本编辑文档的示例，请参阅[写字板](../../visual-cpp-samples.md)示例应用程序。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)

`CRichEditDoc`

## <a name="requirements"></a>要求

**标头：** afxrich.h

##  <a name="createclientitem"></a>  CRichEditDoc::CreateClientItem

调用此函数可创建`CRichEditCntrItem`对象，并将其添加到此文档。

```
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;
```

### <a name="parameters"></a>参数

*preo*<br/>
指向[REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject)结构描述 OLE 项。 新`CRichEditCntrItem`此 OLE 项的周围构造对象。 如果*preo*为 NULL，新的客户端项为空。

### <a name="return-value"></a>返回值

指向新指针[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)已添加到本文档的对象。

### <a name="remarks"></a>备注

此函数不执行任何 OLE 初始化。

有关详细信息，请参阅[REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) Windows SDK 中的结构。

##  <a name="getstreamformat"></a>  CRichEditDoc::GetStreamFormat

调用此函数可确定文本格式的流式处理格式文本编辑的内容。

```
int GetStreamFormat() const;
```

### <a name="return-value"></a>返回值

下列标志之一：

- SF_TEXT 指示 rich edit 控件不维护格式设置信息。

- SF_RTF 指示 rich edit 控件中保存了格式设置信息。

### <a name="remarks"></a>备注

返回值基于[m_bRTF](#m_brtf)数据成员。 如果此函数将返回 SF_RTF`m_bRTF`为 TRUE; 否则为 SF_TEXT。

##  <a name="getview"></a>  CRichEditDoc::GetView

调用此函数可访问[CRichEditView](../../mfc/reference/cricheditview-class.md)与此相关联的对象`CRichEditDoc`对象。

```
virtual CRichEditView* GetView() const;
```

### <a name="return-value"></a>返回值

指向`CRichEditView`与文档关联的对象。

### <a name="remarks"></a>备注

中包含的文本和格式设置信息`CRichEditView`对象。 `CRichEditDoc`对象维护序列化的 OLE 项。 应该只有一个`CRichEditView`为每个`CRichEditDoc`。

##  <a name="m_brtf"></a>  CRichEditDoc::m_bRTF

如果为 TRUE，指示[CRichEditCtrl::StreamIn](../../mfc/reference/cricheditctrl-class.md#streamin)并[CRichEditCtrl::StreamOut](../../mfc/reference/cricheditctrl-class.md#streamout)应存储段落和字符格式设置特征。

```
BOOL m_bRTF;
```

## <a name="see-also"></a>请参阅

[MFC 示例写字板](../../visual-cpp-samples.md)<br/>
[COleServerDoc 类](../../mfc/reference/coleserverdoc-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CRichEditView 类](../../mfc/reference/cricheditview-class.md)<br/>
[CRichEditCntrItem 类](../../mfc/reference/cricheditcntritem-class.md)<br/>
[COleDocument 类](../../mfc/reference/coledocument-class.md)<br/>
[CRichEditCtrl 类](../../mfc/reference/cricheditctrl-class.md)
