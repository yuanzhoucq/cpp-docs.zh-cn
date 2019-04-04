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
ms.openlocfilehash: b348dc2ac68ced89fb0702073f57a114befaf1cb
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58769350"
---
# <a name="cmfcpropertygridfontproperty-class"></a>CMFCPropertyGridFontProperty 类

`CMFCPropertyGridFileProperty`类支持用于打开字体选择对话框中的属性列表控件项。

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
|`CMFCPropertyGridFontProperty::FormatProperty`|设置属性值的文本表示形式的格式。 (重写[cmfcpropertygridproperty:: Formatproperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty)。)|
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|检索用户选择从字体对话框的字体颜色。|
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|检索用户选择从字体对话框的字体。|
|`CMFCPropertyGridFontProperty::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型相关联的对象。|
|`CMFCPropertyGridFontProperty::OnClickButton`|当用户单击属性中包含的按钮时，由框架调用。 (重写[cmfcpropertygridproperty:: Onclickbutton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton)。)|

## <a name="remarks"></a>备注

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)

## <a name="requirements"></a>要求

**标头：** afxpropertygridctrl.h

##  <a name="cmfcpropertygridfontproperty"></a>  CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty

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
[in]属性的名称。

*lf*<br/>
[in]逻辑字体结构，它指定字体的属性。

*dwFontDialogFlags*<br/>
[in]应用于字体对话框中单击属性值下拉列表按钮时显示的样式。 默认值为 CF_EFFECTS 和 CF_SCREENFONTS 的按位组合 (OR)。 有关详细信息，请参阅*标志*的参数[CHOOSEFONT 结构](/windows/desktop/api/commdlg/ns-commdlg-tagchoosefonta)。

*lpszDescr*<br/>
[in]字体属性的说明。 默认值为 NULL。

*dwData*<br/>
[in]特定于应用程序的数据，如整数或与属性关联的其他数据的指针。 默认值为 0。

*color*<br/>
[in]字体的颜色。 默认值为默认颜色。

### <a name="remarks"></a>备注

一个`CMFCPropertyGridFontProperty`对象表示在属性网格字体控件中的字体属性。

### <a name="example"></a>示例

下面的示例演示如何构造的对象`CMFCPropertyGridFontProperty`类。 此示例摘自[新的控件示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]

##  <a name="getcolor"></a>  CMFCPropertyGridFontProperty::GetColor

检索用户选择从字体对话框的字体颜色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

一个表示所选的字体颜色的 RGB 颜色值。

### <a name="remarks"></a>备注

##  <a name="getlogfont"></a>  CMFCPropertyGridFontProperty::GetLogFont

检索用户选择从字体对话框的字体。

```
LPLOGFONT GetLogFont();
```

### <a name="return-value"></a>返回值

一个指向[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)描述所选的字体的结构。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl 类](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty 类](../../mfc/reference/cmfcpropertygridproperty-class.md)
