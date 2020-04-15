---
title: CMFCPropertyGridColorProperty 类
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableAutomaticButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableOtherButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColumnsNumber
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetOriginalValue
helpviewer_keywords:
- CMFCPropertyGridColorProperty [MFC], CMFCPropertyGridColorProperty
- CMFCPropertyGridColorProperty [MFC], EnableAutomaticButton
- CMFCPropertyGridColorProperty [MFC], EnableOtherButton
- CMFCPropertyGridColorProperty [MFC], GetColor
- CMFCPropertyGridColorProperty [MFC], SetColor
- CMFCPropertyGridColorProperty [MFC], SetColumnsNumber
- CMFCPropertyGridColorProperty [MFC], SetOriginalValue
ms.assetid: af37be93-a91e-40a2-9a65-0f3412c6f0f8
ms.openlocfilehash: 62015f384fa5f72ceeceed2605cbf9a6b646a1eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375320"
---
# <a name="cmfcpropertygridcolorproperty-class"></a>CMFCPropertyGridColorProperty 类

`CMFCPropertyGridColorProperty` 类支持用于打开颜色选择对话框的属性列表控件项。

## <a name="syntax"></a>语法

```
class CMFCPropertyGridColorProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty](#cmfcpropertygridcolorproperty)|构造 `CMFCPropertyGridColorProperty` 对象。|
|`CMFCPropertyGridColorProperty::~CMFCPropertyGridColorProperty`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCPropertyGridColorProperty::EnableAutomaticButton](#enableautomaticbutton)|启用颜色选择对话框上的*自动*按钮。 （标准自动按钮标记为**自动**.）|
|[CMFCPropertyGridColorProperty::EnableOtherButton](#enableotherbutton)|启用颜色选择对话框上*的另一个*按钮。 （标准其他按钮标记为**更多颜色**。|
|`CMFCPropertyGridColorProperty::FormatProperty`|设置属性值的文本表示形式的格式。 （覆盖[CMFC 属性网格属性：：格式属性](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).）|
|[CMFC属性网格颜色属性：获取颜色](#getcolor)|获取属性的当前颜色。|
|`CMFCPropertyGridColorProperty::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|`CMFCPropertyGridColorProperty::OnClickButton`|当用户单击属性中包含的按钮时，由框架调用。 （覆盖[CMFC 属性网格属性：：单击按钮](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).）|
|`CMFCPropertyGridColorProperty::OnDrawValue`|由框架调用以显示属性值。 （覆盖[CMFC 属性网格属性：：OnDrawValue](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawvalue).）|
|`CMFCPropertyGridColorProperty::OnEdit`|当用户要修改属性值时由框架调用。 （覆盖[CMFC 属性网格属性：：打开编辑](../../mfc/reference/cmfcpropertygridproperty-class.md#onedit).）|
|`CMFCPropertyGridColorProperty::OnUpdateValue`|当可编辑属性值已更改时由框架调用。 （覆盖[CMFC 属性网格属性：：更新值](../../mfc/reference/cmfcpropertygridproperty-class.md#onupdatevalue).）|
|[CMFCPropertyGridColorProperty::SetColor](#setcolor)|设置属性的新颜色。|
|[CMFCPropertyGridColorProperty::SetColumnsNumber](#setcolumnsnumber)|指定当前颜色属性网格中的列数。|
|[CMFCPropertyGridColorProperty::SetOriginalValue](#setoriginalvalue)|设置可编辑属性的原始值。|

## <a name="remarks"></a>备注

`CMFCPropertyGridColorProperty` 类支持可添加到属性列表控件的颜色属性。 有关详细信息，请参阅[CMFC财产网格Ctrl 类](../../mfc/reference/cmfcpropertygridctrl-class.md)。

## <a name="example"></a>示例

下面的示例演示如何构造 `CMFCPropertyGridColorProperty` 类的对象，以及如何使用 `CMFCPropertyGridColorProperty` 类的各种方法来配置此对象。 下面的代码介绍如何启用“自动”按钮和“其他”按钮，以及如何设置颜色和列数。 此示例是["新控件"示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#13](../../mfc/reference/codesnippet/cpp/cmfcpropertygridcolorproperty-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridColorProperty](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)

## <a name="requirements"></a>要求

**标题：** afxpropertygridctrl.h

## <a name="cmfcpropertygridcolorpropertycmfcpropertygridcolorproperty"></a><a name="cmfcpropertygridcolorproperty"></a>CMFC属性网格颜色属性：CMFC财产网格颜色属性

构造 `CMFCPropertyGridColorProperty` 对象。

```
CMFCPropertyGridColorProperty(
    const CString& strName,
    const COLORREF& color,
    CPalette* pPalette = NULL,
    LPCTSTR lpszDescr = NULL,
    DWORD_PTR dwData = 0);
```

### <a name="parameters"></a>参数

*strName*<br/>
[在]属性的名称。

*颜色*<br/>
[在]属性的颜色值。

*pPalette*<br/>
[在]指向颜色调色板的指针。 默认值为 NULL。

*lpszDescr*<br/>
[在]属性描述。 默认值为 NULL。

*dwData*<br/>
[在]特定于应用程序的数据，例如整数或指向与属性关联的其他数据的指针。 默认值为 0。

## <a name="cmfcpropertygridcolorpropertyenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFC属性网格颜色属性：：启用自动按钮

启用颜色选择对话框上的*自动*按钮。 （标准自动按钮标记为**自动**.）

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
[在]自动按钮的标签文本。

*颜色 自动*<br/>
[在]自动（默认）颜色的 RGB 颜色值。

*b 启用*<br/>
[在]TRUE 启用自动按钮;否则，FALSE。 默认值为 TRUE。

### <a name="remarks"></a>备注

## <a name="cmfcpropertygridcolorpropertyenableotherbutton"></a><a name="enableotherbutton"></a>CMFC属性网格颜色属性：：启用其他按钮

启用颜色选择对话框上*的另一个*按钮。 （标准其他按钮标记为**更多颜色**。

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg = TRUE,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
[在]另一个按钮的标签文本。

*巴尔特·博拉尔德格*<br/>
[在]TRUE 以显示`CMFCColorDialog`对话框;FALSE 以显示标准颜色选择对话框。 默认值为 TRUE。

*b 启用*<br/>
[在]TRUE 以显示其他按钮;否则，FALSE。  默认值为 TRUE。

### <a name="remarks"></a>备注

## <a name="cmfcpropertygridcolorpropertygetcolor"></a><a name="getcolor"></a>CMFC属性网格颜色属性：获取颜色

获取属性的当前颜色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

RGB 颜色值。

### <a name="remarks"></a>备注

## <a name="cmfcpropertygridcolorpropertysetcolor"></a><a name="setcolor"></a>CMFC属性网格颜色属性：：设置颜色

设置属性的新颜色。

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>参数

*颜色*<br/>
[在]RGB 颜色值。

### <a name="remarks"></a>备注

## <a name="cmfcpropertygridcolorpropertysetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFC 属性网格颜色属性：：设置列数

指定当前颜色属性网格中的列数。

```
void SetColumnsNumber(int nColumnsNumber);
```

### <a name="parameters"></a>参数

*n 列数*<br/>
[在]颜色属性网格中的首选列数。

### <a name="remarks"></a>备注

此方法设置`m_nColumnsNumber`受保护数据成员的值。

## <a name="cmfcpropertygridcolorpropertysetoriginalvalue"></a><a name="setoriginalvalue"></a>CMFC属性网格颜色属性：：设置原始值

设置可编辑属性的原始值。

```
virtual void SetOriginalValue(const COleVariant& varValue);
```

### <a name="parameters"></a>参数

*varValue*<br/>
[在]值。

### <a name="remarks"></a>备注

使用[CMFC 属性网格属性：重置原始值](../../mfc/reference/cmfcpropertygridproperty-class.md#resetoriginalvalue)方法重置已编辑属性的原始值。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFC财产网格Ctrl类](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty 类](../../mfc/reference/cmfcpropertygridproperty-class.md)
