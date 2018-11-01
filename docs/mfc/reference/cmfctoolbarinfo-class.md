---
title: CMFCToolBarInfo 类
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo::m_uiColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuResID
helpviewer_keywords:
- CMFCToolBarInfo [MFC], m_uiColdResID
- CMFCToolBarInfo [MFC], m_uiDisabledResID
- CMFCToolBarInfo [MFC], m_uiHotResID
- CMFCToolBarInfo [MFC], m_uiLargeColdResID
- CMFCToolBarInfo [MFC], m_uiLargeDisabledResID
- CMFCToolBarInfo [MFC], m_uiLargeHotResID
- CMFCToolBarInfo [MFC], m_uiMenuDisabledResID
- CMFCToolBarInfo [MFC], m_uiMenuResID
ms.assetid: 6dc84482-eaaa-491f-aa5d-dd7a57886b46
ms.openlocfilehash: e1e460fe3efb5401227e91f49d8f7c4f6689fa27
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651160"
---
# <a name="cmfctoolbarinfo-class"></a>CMFCToolBarInfo 类

包含处于不同状态的工具栏图像的资源 ID。 `CMFCToolBarInfo` 是用作参数的帮助器类[cmfctoolbar:: Loadtoolbarex](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex)方法。

## <a name="syntax"></a>语法

```
class CMFCToolBarInfo
```

## <a name="members"></a>成员

### <a name="data-members"></a>数据成员

|name|描述|
|----------|-----------------|
|[CMFCToolBarInfo::m_uiColdResID](#m_uicoldresid)|包含正则 （冷） 的工具栏图像的工具栏位图的资源 ID。|
|[CMFCToolBarInfo::m_uiDisabledResID](#m_uidisabledresid)|包含已禁用的工具栏图像的工具栏位图的资源 ID。|
|[CMFCToolBarInfo::m_uiHotResID](#m_uihotresid)|包含所选 （热） 工具栏图像的工具栏位图的资源 ID。|
|[CMFCToolBarInfo::m_uiLargeColdResID](#m_uilargecoldresid)|包含大型、 正则工具栏图像的工具栏位图的资源 ID。|
|[CMFCToolBarInfo::m_uiLargeDisabledResID](#m_uilargedisabledresid)|包含很大，工具栏位图的资源 ID 禁用工具栏图像。|
|[CMFCToolBarInfo::m_uiLargeHotResID](#m_uilargehotresid)|用于包含较大、 所选的工具栏图像的工具栏位图的资源 ID。|
|[CMFCToolBarInfo::m_uiMenuDisabledResID](#m_uimenudisabledresid)|包含已禁用的菜单图像的工具栏位图的资源 ID。|
|[CMFCToolBarInfo::m_uiMenuResID](#m_uimenuresid)|包含菜单图像的工具栏位图的资源 ID。|

## <a name="remarks"></a>备注

完整的工具栏位图包含固定大小的小型工具栏图像 （按钮）。 存储在每个资源 ID`CMFCToolBarInfo`对象是包含一套完整的单个状态 （适用于示例中，选择、 已禁用大，或菜单图像） 中的工具栏图像的位图。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)

## <a name="requirements"></a>要求

**标头：** afxtoolbar.h

##  <a name="m_uicoldresid"></a>  CMFCToolBarInfo::m_uiColdResID

指定工具栏的所有常规按钮图像的资源 ID。

```
UINT m_uiColdResID;
```

##  <a name="m_uidisabledresid"></a>  CMFCToolBarInfo::m_uiDisabledResID

指定工具栏的按钮不可用的映像的资源 ID。

```
UINT m_uiDisabledResID;
```

##  <a name="m_uihotresid"></a>  CMFCToolBarInfo::m_uiHotResID

指定工具栏的所有突出显示的按钮图像的资源 ID。

```
UINT m_uiHotResID
```

##  <a name="m_uilargecoldresid"></a>  CMFCToolBarInfo::m_uiLargeColdResID

指定工具栏的所有大型的常规按钮图像的资源 ID。

```
UINT m_uiLargeColdResID
```

##  <a name="m_uilargedisabledresid"></a>  CMFCToolBarInfo::m_uiLargeDisabledResID

指定工具栏的所有大型的禁用的按钮图像的资源 ID。

```
UINT m_uiLargeDisabledResID;
```

##  <a name="m_uilargehotresid"></a>  CMFCToolBarInfo::m_uiLargeHotResID

指定的工具栏上的所有大型突出显示图像的资源 ID。

```
UINT m_uiLargeHotResID;
```

##  <a name="m_uimenudisabledresid"></a>  CMFCToolBarInfo::m_uiMenuDisabledResID

指定工具栏的命令不可用的映像的资源 ID。

```
UINT m_uiMenuDisabledResID;
```

##  <a name="m_uimenuresid"></a>  CMFCToolBarInfo::m_uiMenuResID

指定工具栏的所有常规菜单项图像的资源 ID。

```
UINT m_uiMenuResID;
```

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)
