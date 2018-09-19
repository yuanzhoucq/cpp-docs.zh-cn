---
title: CD2DTextLayout 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::Create
- AFXRENDERTARGET/CD2DTextLayout::Destroy
- AFXRENDERTARGET/CD2DTextLayout::Get
- AFXRENDERTARGET/CD2DTextLayout::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::GetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::IsValid
- AFXRENDERTARGET/CD2DTextLayout::ReCreate
- AFXRENDERTARGET/CD2DTextLayout::SetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::SetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::m_pTextLayout
dev_langs:
- C++
helpviewer_keywords:
- CD2DTextLayout [MFC], CD2DTextLayout
- CD2DTextLayout [MFC], Create
- CD2DTextLayout [MFC], Destroy
- CD2DTextLayout [MFC], Get
- CD2DTextLayout [MFC], GetFontFamilyName
- CD2DTextLayout [MFC], GetLocaleName
- CD2DTextLayout [MFC], IsValid
- CD2DTextLayout [MFC], ReCreate
- CD2DTextLayout [MFC], SetFontFamilyName
- CD2DTextLayout [MFC], SetLocaleName
- CD2DTextLayout [MFC], m_pTextLayout
ms.assetid: 724bd13c-f2ef-4e55-a775-8cb04b7b7908
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a699744955088ad49c0e701166cf368695354fac
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402195"
---
# <a name="cd2dtextlayout-class"></a>CD2DTextLayout 类

IDWriteTextLayout 包装器。

## <a name="syntax"></a>语法

```
class CD2DTextLayout : public CD2DResource;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CD2DTextLayout::CD2DTextLayout](#cd2dtextlayout)|构造一个 CD2DTextLayout 对象。|
|[CD2DTextLayout:: ~ CD2DTextLayout](#cd2dtextlayout__~cd2dtextlayout)|析构函数。 当 D2D 文本布局对象被销毁时调用。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CD2DTextLayout::Create](#create)|创建 CD2DTextLayout。 (重写[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create)。)|
|[CD2DTextLayout::Destroy](#destroy)|销毁 CD2DTextLayout 对象。 (重写[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy)。)|
|[CD2DTextLayout::Get](#get)|返回 IDWriteTextLayout 接口|
|[CD2DTextLayout::GetFontFamilyName](#getfontfamilyname)|复制的指定位置处的文本的字体系列名称。|
|[CD2DTextLayout::GetLocaleName](#getlocalename)|获取指定位置处的文本的区域设置名称。|
|[CD2DTextLayout::IsValid](#isvalid)|检查资源有效性 (重写[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)。)|
|[CD2DTextLayout::ReCreate](#recreate)|重新创建 CD2DTextLayout。 (重写[CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate)。)|
|[CD2DTextLayout::SetFontFamilyName](#setfontfamilyname)|指定的文本范围内的文本的设置以 null 结尾的字体系列名称|
|[CD2DTextLayout::SetLocaleName](#setlocalename)|设置指定的文本范围内的文本的区域设置名称|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CD2DTextLayout::operator IDWriteTextLayout *](#operator_idwritetextlayout_star)|返回 IDWriteTextLayout 接口|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CD2DTextLayout::m_pTextLayout](#m_ptextlayout)|指向 IDWriteTextLayout 的指针。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DTextLayout](../../mfc/reference/cd2dtextlayout-class.md)

## <a name="requirements"></a>要求

**标头：** afxrendertarget.h

##  <a name="_dtorcd2dtextlayout"></a>  CD2DTextLayout:: ~ CD2DTextLayout

析构函数。 当 D2D 文本布局对象被销毁时调用。

```
virtual ~CD2DTextLayout();
```

##  <a name="cd2dtextlayout"></a>  CD2DTextLayout::CD2DTextLayout

构造一个 CD2DTextLayout 对象。

```
CD2DTextLayout(
    CRenderTarget* pParentTarget,
    const CString& strText,
    CD2DTextFormat& textFormat,
    const CD2DSizeF& sizeMax,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>参数

*pParentTarget*<br/>
指向该呈现器目标的指针。

*strText*<br/>
CString 对象包含要创建从新的 CD2DTextLayout 对象的字符串。

*TextFormat*<br/>
CString 对象包含要应用于字符串的格式。

*sizeMax*<br/>
布局框中的大小。

*bAutoDestroy*<br/>
指示所有者 (pParentTarget) 将销毁该对象。

##  <a name="create"></a>  CD2DTextLayout::Create

创建 CD2DTextLayout。

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>返回值

如果该方法成功，它会返回 S_OK。 否则，它返回一个 HRESULT 错误代码。

##  <a name="destroy"></a>  CD2DTextLayout::Destroy

销毁 CD2DTextLayout 对象。

```
virtual void Destroy();
```

##  <a name="get"></a>  CD2DTextLayout::Get

返回 IDWriteTextLayout 接口

```
IDWriteTextLayout* Get();
```

### <a name="return-value"></a>返回值

指向 IDWriteTextLayout 接口或如果对象尚未初始化，则为 NULL 指针。

##  <a name="getfontfamilyname"></a>  CD2DTextLayout::GetFontFamilyName

复制的指定位置处的文本的字体系列名称。

```
CString GetFontFamilyName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>参数

*currentposition 的字段*<br/>
要检查的文本的位置。

*TextRange*<br/>
具有相同的文本范围格式设置为指定 currentposition 的字段的位置处的文本。 这意味着运行都有指定，包括但不是限于字体系列名称的位置的准确格式。

### <a name="return-value"></a>返回值

CString 对象，其中包含当前的字体系列名称。

##  <a name="getlocalename"></a>  CD2DTextLayout::GetLocaleName

获取指定位置处的文本的区域设置名称。

```
CString GetLocaleName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>参数

*currentposition 的字段*<br/>
要检查的文本的位置。

*TextRange*<br/>
具有相同的文本范围格式设置为指定 currentposition 的字段的位置处的文本。 这意味着运行都有指定，包括但不是限于对区域设置名称的位置的准确格式。

### <a name="return-value"></a>返回值

CString 对象，其中包含当前区域设置名称。

##  <a name="isvalid"></a>  CD2DTextLayout::IsValid

检查资源有效性

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>返回值

如果资源是有效，则为，TRUE否则为 FALSE。

##  <a name="m_ptextlayout"></a>  CD2DTextLayout::m_pTextLayout

指向 IDWriteTextLayout 的指针。

```
IDWriteTextLayout* m_pTextLayout;
```

##  <a name="operator_idwritetextlayout_star"></a>  CD2DTextLayout::operator IDWriteTextLayout *

返回 IDWriteTextLayout 接口

```
operator IDWriteTextLayout*();
```

### <a name="return-value"></a>返回值

指向 IDWriteTextLayout 接口或如果对象尚未初始化，则为 NULL 指针。

##  <a name="recreate"></a>  CD2DTextLayout::ReCreate

重新创建 CD2DTextLayout。

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>返回值

如果该方法成功，它会返回 S_OK。 否则，它返回一个 HRESULT 错误代码。

##  <a name="setfontfamilyname"></a>  CD2DTextLayout::SetFontFamilyName

指定的文本范围内的文本的设置以 null 结尾的字体系列名称

```
BOOL SetFontFamilyName(
    LPCWSTR pwzFontFamilyName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>参数

*pwzFontFamilyName*<br/>
适用于整个文本字符串中指定 textRange 的范围的字体系列名称

*TextRange*<br/>
此更改适用的文本范围

### <a name="return-value"></a>返回值

如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE

##  <a name="setlocalename"></a>  CD2DTextLayout::SetLocaleName

设置指定的文本范围内的文本的区域设置名称

```
BOOL SetLocaleName(
    LPCWSTR pwzLocaleName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>参数

*pwzLocaleName*<br/>
以 null 结尾的区域设置名称字符串

*TextRange*<br/>
此更改适用的文本范围

### <a name="return-value"></a>返回值

如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
