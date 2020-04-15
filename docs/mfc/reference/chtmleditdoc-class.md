---
title: CHtmlEditDoc 类
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditDoc
- AFXHTML/CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::GetView
- AFXHTML/CHtmlEditDoc::IsModified
- AFXHTML/CHtmlEditDoc::OpenURL
helpviewer_keywords:
- CHtmlEditDoc [MFC], CHtmlEditDoc
- CHtmlEditDoc [MFC], GetView
- CHtmlEditDoc [MFC], IsModified
- CHtmlEditDoc [MFC], OpenURL
ms.assetid: b2cca61f-e5d6-4099-b0d1-46bf85f0bd64
ms.openlocfilehash: 8b500f651da1a73040fdb0469f2f023babe25e85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352165"
---
# <a name="chtmleditdoc-class"></a>CHtmlEditDoc 类

使用[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)，在 MFC 文档视图体系结构的上下文中提供 Web 浏览器编辑平台的功能。

## <a name="syntax"></a>语法

```
class AFX_NOVTABLE CHtmlEditDoc : public CDocument
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CHtml编辑文件：CHtml编辑多克](#chtmleditdoc)|构造 `CHtmlEditDoc` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CHtml编辑文件：获取视图](#getview)|检索附加到此`CHtmlEditView`文档的对象。|
|[CHtmlEditDoc：已修改](#ismodified)|返回关联的视图的 WebBrowser 控件是否包含用户已修改的文档。|
|[CHtml编辑文件：：打开URL](#openurl)|打开 URL。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`CHtmlEditDoc`

## <a name="requirements"></a>要求

**标头：** afxhtml.h

## <a name="chtmleditdocchtmleditdoc"></a><a name="chtmleditdoc"></a>CHtml编辑文件：CHtml编辑多克

构造 `CHtmlEditDoc` 对象。

```
CHtmlEditDoc();
```

## <a name="chtmleditdocgetview"></a><a name="getview"></a>CHtml编辑文件：获取视图

检索附加到本文档的[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)对象。

```
virtual CHtmlEditView* GetView() const;
```

### <a name="return-value"></a>返回值

返回指向文档`CHtmlEditView`对象的指针。

## <a name="chtmleditdocismodified"></a><a name="ismodified"></a>CHtmlEditDoc：已修改

返回关联的视图的 WebBrowser 控件是否包含用户已修改的文档。

```
virtual BOOL IsModified();
```

## <a name="chtmleditdocopenurl"></a><a name="openurl"></a>CHtml编辑文件：：打开URL

打开 URL。

```
virtual BOOL OpenURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>参数

*lpszURL*<br/>
要打开的 URL。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="see-also"></a>另请参阅

[HTML编辑示例](../../overview/visual-cpp-samples.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
