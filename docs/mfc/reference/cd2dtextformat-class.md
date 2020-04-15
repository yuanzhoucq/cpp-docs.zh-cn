---
title: CD2DTextFormat 类
ms.date: 03/27/2019
f1_keywords:
- CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat::CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat::Create
- AFXRENDERTARGET/CD2DTextFormat::Destroy
- AFXRENDERTARGET/CD2DTextFormat::Get
- AFXRENDERTARGET/CD2DTextFormat::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextFormat::GetLocaleName
- AFXRENDERTARGET/CD2DTextFormat::IsValid
- AFXRENDERTARGET/CD2DTextFormat::ReCreate
- AFXRENDERTARGET/CD2DTextFormat::m_pTextFormat
helpviewer_keywords:
- CD2DTextFormat [MFC], CD2DTextFormat
- CD2DTextFormat [MFC], Create
- CD2DTextFormat [MFC], Destroy
- CD2DTextFormat [MFC], Get
- CD2DTextFormat [MFC], GetFontFamilyName
- CD2DTextFormat [MFC], GetLocaleName
- CD2DTextFormat [MFC], IsValid
- CD2DTextFormat [MFC], ReCreate
- CD2DTextFormat [MFC], m_pTextFormat
ms.assetid: db194cec-9dae-4644-ab84-7c43b7164117
ms.openlocfilehash: f7310fd3ca2ac34df7cc1a99cd5527ea8ba709c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369038"
---
# <a name="cd2dtextformat-class"></a>CD2DTextFormat 类

IDWriteText格式的包装。

## <a name="syntax"></a>语法

```
class CD2DTextFormat : public CD2DResource;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CD2D文本格式：CD2D文本格式](#cd2dtextformat)|构造 CD2DText格式对象。|
|[CD2D文本格式：*CD2D文本格式](#_dtorcd2dtextformat)|析构函数。 销毁 D2D 文本格式对象时调用。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CD2D文本格式：创建](#create)|创建 CD2D 文本格式。 （覆盖[CD2D 资源：创建](../../mfc/reference/cd2dresource-class.md#create).）|
|[CD2D文本格式：:D](#destroy)|销毁 CD2DText 格式对象。 （覆盖[CD2D 资源：:D）](../../mfc/reference/cd2dresource-class.md#destroy)|
|[CD2D文本格式：获取](#get)|返回 IDWriteText格式接口|
|[CD2D文本格式：：获取方特家庭名称](#getfontfamilyname)|获取字体姓氏的副本。|
|[CD2D文本格式：获取本地化名称](#getlocalename)|获取区域设置名称的副本。|
|[CD2D文本格式：：有效](#isvalid)|检查资源有效性（覆盖[CD2D 资源：：有效](../../mfc/reference/cd2dresource-class.md#isvalid)。）|
|[CD2D文本格式：重新创建](#recreate)|重新创建 CD2D 文本格式。 （覆盖[CD2D 资源：：重新创建](../../mfc/reference/cd2dresource-class.md#recreate).）|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CD2D文本格式：：操作员 IDWriteText 格式*](#operator_idwritetextformat_star)|返回 IDWriteText格式接口|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CD2D文本格式：：m_pTextFormat](#m_ptextformat)|指向 IDWriteText 格式的指针。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 资源](../../mfc/reference/cd2dresource-class.md)

[CD2D文本格式](../../mfc/reference/cd2dtextformat-class.md)

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2dtextformatcd2dtextformat"></a><a name="_dtorcd2dtextformat"></a>CD2D文本格式：*CD2D文本格式

析构函数。 销毁 D2D 文本格式对象时调用。

```
virtual ~CD2DTextFormat();
```

## <a name="cd2dtextformatcd2dtextformat"></a><a name="cd2dtextformat"></a>CD2D文本格式：CD2D文本格式

构造 CD2DText格式对象。

```
CD2DTextFormat(
    CRenderTarget* pParentTarget,
    const CString& strFontFamilyName,
    FLOAT fontSize,
    DWRITE_FONT_WEIGHT fontWeight = DWRITE_FONT_WEIGHT_NORMAL,
    DWRITE_FONT_STYLE fontStyle = DWRITE_FONT_STYLE_NORMAL,
    DWRITE_FONT_STRETCH fontStretch = DWRITE_FONT_STRETCH_NORMAL,
    const CString& strFontLocale = _T(""),
    IDWriteFontCollection* pFontCollection = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>参数

*p 父目标*<br/>
指向渲染目标的指针。

*斯特方特家族名称*<br/>
包含字体系列名称的 CString 对象。

*字体大小*<br/>
以 DIP（"与设备无关的像素"）为单位的字体的逻辑大小。 DIP 等于 1/96 英寸。

*字体重量*<br/>
指示文本对象的字体粗细的值。

*字体样式*<br/>
指示文本对象的字体样式的值。

*字体拉伸*<br/>
指示文本对象的字体拉伸的值。

*斯特方特拉兹*<br/>
包含区域设置名称的 CString 对象。

*pFontCollection*<br/>
指向字体集合对象的指针。 当为 NULL 时，指示系统字体收集。

*bAuto销毁*<br/>
指示对象将被所有者（pParentTarget）销毁。

## <a name="cd2dtextformatcreate"></a><a name="create"></a>CD2D文本格式：创建

创建 CD2D 文本格式。

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回一个 HRESULT 错误代码。

## <a name="cd2dtextformatdestroy"></a><a name="destroy"></a>CD2D文本格式：:D

销毁 CD2DText 格式对象。

```
virtual void Destroy();
```

## <a name="cd2dtextformatget"></a><a name="get"></a>CD2D文本格式：获取

返回 IDWriteText格式接口

```
IDWriteTextFormat* Get();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 IDWriteTextFormat 接口或 NULL 的指针。

## <a name="cd2dtextformatgetfontfamilyname"></a><a name="getfontfamilyname"></a>CD2D文本格式：：获取方特家庭名称

获取字体姓氏的副本。

```
CString GetFontFamilyName() const;
```

### <a name="return-value"></a>返回值

包含当前字体族名的 CString 对象。

## <a name="cd2dtextformatgetlocalename"></a><a name="getlocalename"></a>CD2D文本格式：获取本地化名称

获取区域设置名称的副本。

```
CString GetLocaleName() const;
```

### <a name="return-value"></a>返回值

包含当前区域设置名称的 CString 对象。

## <a name="cd2dtextformatisvalid"></a><a name="isvalid"></a>CD2D文本格式：：有效

检查资源有效性

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>返回值

如果资源有效，则为 TRUE;否则 FALSE。

## <a name="cd2dtextformatm_ptextformat"></a><a name="m_ptextformat"></a>CD2D文本格式：：m_pTextFormat

指向 IDWriteText 格式的指针。

```
IDWriteTextFormat* m_pTextFormat;
```

## <a name="cd2dtextformatoperator-idwritetextformat"></a><a name="operator_idwritetextformat_star"></a>CD2D文本格式：：操作员 IDWriteText 格式*

返回 IDWriteText格式接口

```
operator IDWriteTextFormat*();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 IDWriteTextFormat 接口或 NULL 的指针。

## <a name="cd2dtextformatrecreate"></a><a name="recreate"></a>CD2D文本格式：重新创建

重新创建 CD2D 文本格式。

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回一个 HRESULT 错误代码。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
