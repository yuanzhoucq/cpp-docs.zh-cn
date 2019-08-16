---
title: CMFCPropertyGridFontProperty 类
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetLogFont
helpviewer_keywords:
- CMFCPropertyGridFontProperty [MFC], CMFCPropertyGridFontProperty
- CMFCPropertyGridFontProperty [MFC], GetColor
- CMFCPropertyGridFontProperty [MFC], GetLogFont
ms.assetid: 83693f33-bbd3-4fcb-a9ad-fa79fcf2ca24
ms.openlocfilehash: a3c5b806482a97d64a9ffab92877781cb8778b6b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505111"
---
# <a name="cmfcpropertygridfontproperty-class"></a>CMFCPropertyGridFontProperty 类

`CMFCPropertyGridFileProperty`类支持打开字体选择对话框的属性列表控件项。

## <a name="syntax"></a>语法

```
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](#cmfcpropertygridfontproperty)|构造 `CMFCPropertyGridFontProperty` 对象。|
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|`CMFCPropertyGridFontProperty::FormatProperty`|设置属性值的文本表示形式的格式。 (重写[CMFCPropertyGridProperty:: FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty)。)|
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|检索用户从 "字体" 对话框中选择的字体颜色。|
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|检索用户从 "字体" 对话框中选择的字体。|
|`CMFCPropertyGridFontProperty::GetThisClass`|由框架用于获取指向与此类类型相关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|`CMFCPropertyGridFontProperty::OnClickButton`|当用户单击属性中包含的按钮时，由框架调用。 (重写[CMFCPropertyGridProperty:: OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton)。)|

## <a name="remarks"></a>备注

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)

## <a name="requirements"></a>要求

**标头:** afxpropertygridctrl

##  <a name="cmfcpropertygridfontproperty"></a>CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty

构造 `CMFCPropertyGridFontProperty` 对象。

```
CMFCPropertyGridFontProperty(
    const CString& strName,
    LOGFONT& lf,
    DWORD dwFontDialogFlags = CF_EFFECTS | CF_SCREENFONTS,
    LPCTSTR lpszDescr = NULL,
    DWORD_PTR dwData = 0,
    COLORREF color = (COLORREF)-1);
```

### <a name="parameters"></a>参数

*strName*<br/>
中属性的名称。

*lf*<br/>
中指定字体特性的逻辑字体结构。

*dwFontDialogFlags*<br/>
中应用于在单击 "属性值" 下拉按钮时显示的 "字体" 对话框的样式。 默认值为 CF_EFFECTS 和 CF_SCREENFONTS 的按位组合 (OR)。 有关详细信息, 请参阅[CHOOSEFONT 结构](/windows/win32/api/commdlg/ns-commdlg-choosefontw)的*Flags*参数。

*lpszDescr*<br/>
中Font 属性的说明。 默认值为 NULL。

*dwData*<br/>
中应用程序特定的数据, 例如一个整数或指向与属性关联的其他数据的指针。 默认值为 0。

*color*<br/>
中字体的颜色。 默认值为默认颜色。

### <a name="remarks"></a>备注

`CMFCPropertyGridFontProperty`对象表示属性网格字体控件中的字体属性。

### <a name="example"></a>示例

下面的示例演示如何构造`CMFCPropertyGridFontProperty`类的对象。 此示例是[新控件示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]

##  <a name="getcolor"></a>CMFCPropertyGridFontProperty:: GetColor

检索用户从 "字体" 对话框中选择的字体颜色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

表示选定字体颜色的 RGB 颜色值。

### <a name="remarks"></a>备注

##  <a name="getlogfont"></a>CMFCPropertyGridFontProperty::GetLogFont

检索用户从 "字体" 对话框中选择的字体。

```
LPLOGFONT GetLogFont();
```

### <a name="return-value"></a>返回值

指向描述选定字体的[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)结构的指针。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl 类](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty 类](../../mfc/reference/cmfcpropertygridproperty-class.md)
