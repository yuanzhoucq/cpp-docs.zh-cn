---
title: CD2DTextLayout 类
ms.date: 03/27/2019
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
ms.openlocfilehash: 9be4c1134e2f82ceb3af31cbeb1a7d55f4071777
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369030"
---
# <a name="cd2dtextlayout-class"></a>CD2DTextLayout 类

IDWriteTextLayout 的包装器。

## <a name="syntax"></a>语法

```
class CD2DTextLayout : public CD2DResource;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CD2D文本布局：：CD2D文本布局](#cd2dtextlayout)|构造 CD2DTextLayout 对象。|
|[CD2D文本布局：：~CD2D文本布局](#_dtorcd2dtextlayout)|析构函数。 销毁 D2D 文本布局对象时调用。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CD2D文本布局：：创建](#create)|创建 CD2D 文本布局。 （覆盖[CD2D 资源：创建](../../mfc/reference/cd2dresource-class.md#create).）|
|[CD2D文本布局：:D](#destroy)|销毁 CD2DTextLayout 对象。 （覆盖[CD2D 资源：:D）](../../mfc/reference/cd2dresource-class.md#destroy)|
|[CD2D文本布局：：获取](#get)|返回 IDWrite 文本布局界面|
|[CD2D文本布局：：获取方特家族名称](#getfontfamilyname)|在指定位置复制文本的字体族名。|
|[CD2D文本布局：：获取本地化名称](#getlocalename)|在指定位置获取文本的区域设置名称。|
|[CD2D文本布局：：有效](#isvalid)|检查资源有效性（覆盖[CD2D 资源：：有效](../../mfc/reference/cd2dresource-class.md#isvalid)。）|
|[CD2D文本布局：：重新创建](#recreate)|重新创建 CD2D 文本布局。 （覆盖[CD2D 资源：：重新创建](../../mfc/reference/cd2dresource-class.md#recreate).）|
|[CD2D文本布局：：设置字体家庭名称](#setfontfamilyname)|为指定文本范围内的文本设置 null 端接字体族名|
|[CD2D 文本布局：：设置本地化名称](#setlocalename)|设置指定文本范围内文本的区域设置名称|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CD2D文本布局：：操作员 IDWriteTextLayout*](#operator_idwritetextlayout_star)|返回 IDWrite 文本布局界面|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CD2D文本布局：：m_pTextLayout](#m_ptextlayout)|指向 IDWriteTextLayout 的指针。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 资源](../../mfc/reference/cd2dresource-class.md)

[CD2D文本布局](../../mfc/reference/cd2dtextlayout-class.md)

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2dtextlayoutcd2dtextlayout"></a><a name="_dtorcd2dtextlayout"></a>CD2D文本布局：：~CD2D文本布局

析构函数。 销毁 D2D 文本布局对象时调用。

```
virtual ~CD2DTextLayout();
```

## <a name="cd2dtextlayoutcd2dtextlayout"></a><a name="cd2dtextlayout"></a>CD2D文本布局：：CD2D文本布局

构造 CD2DTextLayout 对象。

```
CD2DTextLayout(
    CRenderTarget* pParentTarget,
    const CString& strText,
    CD2DTextFormat& textFormat,
    const CD2DSizeF& sizeMax,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>参数

*p 父目标*<br/>
指向渲染目标的指针。

*斯特文本*<br/>
包含要从中创建新 CD2DTextLayout 对象的 CString 对象。

*textFormat*<br/>
包含要应用于字符串的格式的 CString 对象。

*大小最大*<br/>
布局框的大小。

*bAuto销毁*<br/>
指示对象将被所有者（pParentTarget）销毁。

## <a name="cd2dtextlayoutcreate"></a><a name="create"></a>CD2D文本布局：：创建

创建 CD2D 文本布局。

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回一个 HRESULT 错误代码。

## <a name="cd2dtextlayoutdestroy"></a><a name="destroy"></a>CD2D文本布局：:D

销毁 CD2DTextLayout 对象。

```
virtual void Destroy();
```

## <a name="cd2dtextlayoutget"></a><a name="get"></a>CD2D文本布局：：获取

返回 IDWrite 文本布局界面

```
IDWriteTextLayout* Get();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 IDWriteTextLayout 接口或 NULL 的指针。

## <a name="cd2dtextlayoutgetfontfamilyname"></a><a name="getfontfamilyname"></a>CD2D文本布局：：获取方特家族名称

在指定位置复制文本的字体族名。

```
CString GetFontFamilyName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>参数

*电流位置*<br/>
要检查的文本的位置。

*文本范围*<br/>
与当前位置指定位置的文本具有相同格式的文本范围。 这意味着运行具有指定位置的精确格式，包括但不限于字体族名。

### <a name="return-value"></a>返回值

包含当前字体族名的 CString 对象。

## <a name="cd2dtextlayoutgetlocalename"></a><a name="getlocalename"></a>CD2D文本布局：：获取本地化名称

在指定位置获取文本的区域设置名称。

```
CString GetLocaleName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>参数

*电流位置*<br/>
要检查的文本的位置。

*文本范围*<br/>
与当前位置指定位置的文本具有相同格式的文本范围。 这意味着运行具有指定位置的精确格式，包括但不限于区域设置名称。

### <a name="return-value"></a>返回值

包含当前区域设置名称的 CString 对象。

## <a name="cd2dtextlayoutisvalid"></a><a name="isvalid"></a>CD2D文本布局：：有效

检查资源有效性

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>返回值

如果资源有效，则为 TRUE;否则 FALSE。

## <a name="cd2dtextlayoutm_ptextlayout"></a><a name="m_ptextlayout"></a>CD2D文本布局：：m_pTextLayout

指向 IDWriteTextLayout 的指针。

```
IDWriteTextLayout* m_pTextLayout;
```

## <a name="cd2dtextlayoutoperator-idwritetextlayout"></a><a name="operator_idwritetextlayout_star"></a>CD2D文本布局：：操作员 IDWriteTextLayout*

返回 IDWrite 文本布局界面

```
operator IDWriteTextLayout*();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 IDWriteTextLayout 接口或 NULL 的指针。

## <a name="cd2dtextlayoutrecreate"></a><a name="recreate"></a>CD2D文本布局：：重新创建

重新创建 CD2D 文本布局。

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回一个 HRESULT 错误代码。

## <a name="cd2dtextlayoutsetfontfamilyname"></a><a name="setfontfamilyname"></a>CD2D文本布局：：设置字体家庭名称

为指定文本范围内的文本设置 null 端接字体族名

```
BOOL SetFontFamilyName(
    LPCWSTR pwzFontFamilyName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>参数

*pwzFont家族名称*<br/>
应用于文本Range 指定范围内的整个文本字符串的字体族名

*文本范围*<br/>
此更改应用于的文本范围

### <a name="return-value"></a>返回值

如果该方法成功，它将返回 TRUE。 否则，它将返回 FALSE

## <a name="cd2dtextlayoutsetlocalename"></a><a name="setlocalename"></a>CD2D 文本布局：：设置本地化名称

设置指定文本范围内文本的区域设置名称

```
BOOL SetLocaleName(
    LPCWSTR pwzLocaleName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>参数

*pwzLocale名称*<br/>
空终止区域设置名称字符串

*文本范围*<br/>
此更改应用于的文本范围

### <a name="return-value"></a>返回值

如果该方法成功，它将返回 TRUE。 否则，它将返回 FALSE

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
