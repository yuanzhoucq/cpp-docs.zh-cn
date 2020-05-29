---
title: CMFCRibbonLabel 类
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::SetACCData
helpviewer_keywords:
- CMFCRibbonLabel [MFC], CMFCRibbonLabel
- CMFCRibbonLabel [MFC], SetACCData
ms.assetid: 0346c891-83bf-4f20-b8a1-c84cf2aadced
ms.openlocfilehash: cd30e374441661368d3ea7abf5177424f8dffb3c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375126"
---
# <a name="cmfcribbonlabel-class"></a>CMFCRibbonLabel 类

实现功能区的不可单击文本标签。

## <a name="syntax"></a>语法

```
class CMFCRibbonLabel : public CMFCRibbonButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC带标签：：CMFC带标签](#cmfcribbonlabel)|使用指定的文本字符串构造和初始`CMFCRibbonLabel`化对象。|
|`CMFCRibbonLabel::~CMFCRibbonLabel`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|`CMFCRibbonLabel::CreateObject`|由框架用于创建此类类型的动态实例。|
|`CMFCRibbonLabel::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFC 功能标签：：设置ACC数据](#setaccdata)|确定当前功能区标签元素的辅助功能数据。 （覆盖[CMFC 功能按钮：设置ACC数据](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).）|

### <a name="remarks"></a>备注

创建功能区标签后，请调用[CMFC 功能面板：：：添加](../../mfc/reference/cmfcribbonpanel-class.md#add)，将其添加到面板中。

不能向"快速访问"工具栏添加功能区标签。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)

## <a name="requirements"></a>要求

**标题：** afxRibbonLabel.h

## <a name="cmfcribbonlabelcmfcribbonlabel"></a><a name="cmfcribbonlabel"></a>CMFC带标签：：CMFC带标签

构造并初始化显示指定文本字符串的[CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)对象。

```
CMFCRibbonLabel(
    LPCTSTR lpszText,
    BOOL bIsMultiLine = FALSE);
```

### <a name="parameters"></a>参数

*lpszText*<br/>
[在]要显示在标签中的文本。

*bIs多行*<br/>
[在]TRUE 指定标签是多行标签;否则，FALSE。

## <a name="cmfcribbonlabelsetaccdata"></a><a name="setaccdata"></a>CMFC 功能标签：：设置ACC数据

确定当前功能区标签元素的辅助功能数据。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>参数

*p 父级*<br/>
[在]表示当前功能区标签的父窗口。

*数据*<br/>
[出]使用当前功能区`CAccessibilityData`标签的辅助功能数据的填充的类型对象。

### <a name="return-value"></a>返回值

如果*数据*参数已成功填充当前功能区标签的辅助功能数据，则为 TRUE;否则，FALSE。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFC 功能按钮类](../../mfc/reference/cmfcribbonbutton-class.md)
