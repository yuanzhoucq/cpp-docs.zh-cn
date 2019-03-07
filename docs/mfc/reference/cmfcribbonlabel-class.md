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
ms.openlocfilehash: b79d6191d2deb0a295e81da1150cc7b38fd81232
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283453"
---
# <a name="cmfcribbonlabel-class"></a>CMFCRibbonLabel 类

实现功能区的不可单击文本标签。

## <a name="syntax"></a>语法

```
class CMFCRibbonLabel : public CMFCRibbonButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCRibbonLabel::CMFCRibbonLabel](#cmfcribbonlabel)|构造并初始化`CMFCRibbonLabel`对象与指定的文本字符串。|
|`CMFCRibbonLabel::~CMFCRibbonLabel`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|`CMFCRibbonLabel::CreateObject`|由框架用于创建此类类型的动态实例。|
|`CMFCRibbonLabel::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型相关联的对象。|
|[CMFCRibbonLabel::SetACCData](#setaccdata)|确定当前的功能区标签元素的可访问性数据。 (重写[cmfcribbonbutton:: Setaccdata](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata)。)|

### <a name="remarks"></a>备注

创建功能区标签后，将其添加到一个面板，通过调用[cmfcribbonpanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add)。

无法将功能区标签添加到快速访问工具栏。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)

## <a name="requirements"></a>要求

**标头：** afxRibbonLabel.h

##  <a name="cmfcribbonlabel"></a>  CMFCRibbonLabel::CMFCRibbonLabel

构造并初始化[CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)显示指定的文本字符串的对象。

```
CMFCRibbonLabel(
    LPCTSTR lpszText,
    BOOL bIsMultiLine = FALSE);
```

### <a name="parameters"></a>参数

*lpszText*<br/>
[in]要在标签中显示的文本。

*bIsMultiLine*<br/>
[in]若要指定标签是一个多行标签;，则返回 TRUE否则为 FALSE。

##  <a name="setaccdata"></a>  CMFCRibbonLabel::SetACCData

确定当前的功能区标签元素的可访问性数据。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>参数

*pParent*<br/>
[in]表示父窗口的当前功能区标签。

*data*<br/>
[out]类型的对象`CAccessibilityData`填入的可访问性数据的当前功能区标签。

### <a name="return-value"></a>返回值

则为 TRUE*数据*参数已成功使用当前的功能区标签可访问性数据填充; 否则为 FALSE。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton 类](../../mfc/reference/cmfcribbonbutton-class.md)
