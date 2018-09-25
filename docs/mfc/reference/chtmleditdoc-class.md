---
title: CHtmlEditDoc 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CHtmlEditDoc
- AFXHTML/CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::GetView
- AFXHTML/CHtmlEditDoc::IsModified
- AFXHTML/CHtmlEditDoc::OpenURL
dev_langs:
- C++
helpviewer_keywords:
- CHtmlEditDoc [MFC], CHtmlEditDoc
- CHtmlEditDoc [MFC], GetView
- CHtmlEditDoc [MFC], IsModified
- CHtmlEditDoc [MFC], OpenURL
ms.assetid: b2cca61f-e5d6-4099-b0d1-46bf85f0bd64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 77219f4cac64faf2604c427a2c4abf3babfd26a3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425351"
---
# <a name="chtmleditdoc-class"></a>CHtmlEditDoc 类

与[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)，提供 MFC 文档视图体系结构上下文中的 WebBrowser 编辑平台功能。

## <a name="syntax"></a>语法

```
class AFX_NOVTABLE CHtmlEditDoc : public CDocument
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CHtmlEditDoc::CHtmlEditDoc](#chtmleditdoc)|构造 `CHtmlEditDoc` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CHtmlEditDoc::GetView](#getview)|检索`CHtmlEditView`对象附加到此文档。|
|[CHtmlEditDoc::IsModified](#ismodified)|返回关联的视图的 WebBrowser 控件是否包含已由用户修改的文档。|
|[CHtmlEditDoc::OpenURL](#openurl)|将打开一个 URL。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`CHtmlEditDoc`

## <a name="requirements"></a>要求

**标头：** afxhtml.h

##  <a name="chtmleditdoc"></a>  CHtmlEditDoc::CHtmlEditDoc

构造 `CHtmlEditDoc` 对象。

```
CHtmlEditDoc();
```

##  <a name="getview"></a>  CHtmlEditDoc::GetView

检索[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)对象附加到此文档。

```
virtual CHtmlEditView* GetView() const;
```

### <a name="return-value"></a>返回值

返回一个指向文档的`CHtmlEditView`对象。

##  <a name="ismodified"></a>  CHtmlEditDoc::IsModified

返回关联的视图的 WebBrowser 控件是否包含已由用户修改的文档。

```
virtual BOOL IsModified();
```

##  <a name="openurl"></a>  CHtmlEditDoc::OpenURL

将打开一个 URL。

```
virtual BOOL OpenURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>参数

*lpszURL*<br/>
要打开的 URL。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

## <a name="see-also"></a>请参阅

[HTMLEdit 示例](../../visual-cpp-samples.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)

