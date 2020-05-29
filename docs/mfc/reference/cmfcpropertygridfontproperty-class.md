---
title: CMFC财产网格方瑟属性类
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
ms.openlocfilehash: a1c9905d8d7f32a049496c4e164c9eaac13455d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361840"
---
# <a name="cmfcpropertygridfontproperty-class"></a>CMFC财产网格方瑟属性类

类`CMFCPropertyGridFileProperty`支持打开字体选择对话框的属性列表控件项。

## <a name="syntax"></a>语法

```
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC财产网格方瑟财产：CMFC财产网格方瑟财产](#cmfcpropertygridfontproperty)|构造 `CMFCPropertyGridFontProperty` 对象。|
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|`CMFCPropertyGridFontProperty::FormatProperty`|设置属性值的文本表示形式的格式。 （覆盖[CMFC 属性网格属性：：格式属性](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).）|
|[CMFC财产网格方属性：获取颜色](#getcolor)|检索用户从字体对话框中选择的字体颜色。|
|[CMFC财产网格方瑟财产：获取日志字体](#getlogfont)|检索用户从字体对话框中选择的字体。|
|`CMFCPropertyGridFontProperty::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|`CMFCPropertyGridFontProperty::OnClickButton`|当用户单击属性中包含的按钮时，由框架调用。 （覆盖[CMFC 属性网格属性：：单击按钮](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).）|

## <a name="remarks"></a>备注

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)

## <a name="requirements"></a>要求

**标题：** afxpropertygridctrl.h

## <a name="cmfcpropertygridfontpropertycmfcpropertygridfontproperty"></a><a name="cmfcpropertygridfontproperty"></a>CMFC财产网格方瑟财产：CMFC财产网格方瑟财产

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
[在]属性的名称。

*如果*<br/>
[在]指定字体属性的逻辑字体结构。

*dwFontDialogFlags*<br/>
[在]应用于单击属性值下拉按钮时显示的字体对话框的样式。 默认值是CF_EFFECTS和CF_SCREENFONTS的位组合 （OR）。 有关详细信息，请参阅[CHOOSEFONT 结构](/windows/win32/api/commdlg/ns-commdlg-choosefontw)*的标志参数。*

*lpszDescr*<br/>
[在]字体属性的说明。 默认值为 NULL。

*dwData*<br/>
[在]特定于应用程序的数据，例如整数或指向与属性关联的其他数据的指针。 默认值为 0。

*颜色*<br/>
[在]字体的颜色。 默认值为默认颜色。

### <a name="remarks"></a>备注

对象`CMFCPropertyGridFontProperty`表示属性网格字体控件中的字体属性。

### <a name="example"></a>示例

下面的示例演示如何构造`CMFCPropertyGridFontProperty`类的对象。 此示例是["新控件"示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]

## <a name="cmfcpropertygridfontpropertygetcolor"></a><a name="getcolor"></a>CMFC财产网格方属性：获取颜色

检索用户从字体对话框中选择的字体颜色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

表示所选字体颜色的 RGB 颜色值。

### <a name="remarks"></a>备注

## <a name="cmfcpropertygridfontpropertygetlogfont"></a><a name="getlogfont"></a>CMFC财产网格方瑟财产：获取日志字体

检索用户从字体对话框中选择的字体。

```
LPLOGFONT GetLogFont();
```

### <a name="return-value"></a>返回值

指向描述所选字体的[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)结构的指针。

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFC财产网格Ctrl类](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty 类](../../mfc/reference/cmfcpropertygridproperty-class.md)
