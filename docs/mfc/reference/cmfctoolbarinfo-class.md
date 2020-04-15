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
ms.openlocfilehash: 593d1665751f7322fc2a9cee307620df88d46876
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376195"
---
# <a name="cmfctoolbarinfo-class"></a>CMFCToolBarInfo 类

包含处于不同状态的工具栏图像的资源 ID。 `CMFCToolBarInfo`是用作[CMFCToolBar：：LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex)方法参数的帮助器类。

## <a name="syntax"></a>语法

```
class CMFCToolBarInfo
```

## <a name="members"></a>成员

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|[CMFCToolBarinfo：m_uiColdResID](#m_uicoldresid)|包含常规（冷）工具栏图像的工具栏位图的资源 ID。|
|[CMFCToolBarinfo：m_uiDisabledResID](#m_uidisabledresid)|包含禁用工具栏图像的工具栏位图的资源 ID。|
|[CMFCToolBarinfo：m_uiHotResID](#m_uihotresid)|包含所选（热）工具栏图像的工具栏位图的资源 ID。|
|[CMFCToolBarInfo：m_uiLargeColdResID](#m_uilargecoldresid)|包含大型常规工具栏图像的工具栏位图的资源 ID。|
|[CMFCToolBarInfo：m_uiLargeDisabledResID](#m_uilargedisabledresid)|包含大型禁用工具栏图像的工具栏位图的资源 ID。|
|[CMFCToolBarInfo：m_uiLargeHotResID](#m_uilargehotresid)|包含大型选定工具栏图像的工具栏位图的资源 ID。|
|[CMFCToolBarinfo：m_uiMenuDisabledResID](#m_uimenudisabledresid)|包含禁用菜单图像的工具栏位图的资源 ID。|
|[CMFCToolBarinfo：m_uiMenuResID](#m_uimenuresid)|包含菜单图像的工具栏位图的资源 ID。|

## <a name="remarks"></a>备注

完整的工具栏位图由固定大小的小工具栏图像（按钮）组成。 存储在`CMFCToolBarInfo`对象中的每个资源 ID 都是一个位图，其中包含一组处于单一状态的工具栏图像（例如，选定、禁用、大型或菜单图像）。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)

## <a name="requirements"></a>要求

**标题：** afxtoolbar.h

## <a name="cmfctoolbarinfom_uicoldresid"></a><a name="m_uicoldresid"></a>CMFCToolBarinfo：m_uiColdResID

为工具栏的所有常规按钮图像指定资源 ID。

```
UINT m_uiColdResID;
```

## <a name="cmfctoolbarinfom_uidisabledresid"></a><a name="m_uidisabledresid"></a>CMFCToolBarinfo：m_uiDisabledResID

为工具栏的按钮不可用图像指定资源 ID。

```
UINT m_uiDisabledResID;
```

## <a name="cmfctoolbarinfom_uihotresid"></a><a name="m_uihotresid"></a>CMFCToolBarinfo：m_uiHotResID

为工具栏的所有突出显示的按钮图像指定资源 ID。

```
UINT m_uiHotResID
```

## <a name="cmfctoolbarinfom_uilargecoldresid"></a><a name="m_uilargecoldresid"></a>CMFCToolBarInfo：m_uiLargeColdResID

为工具栏的所有大型常规按钮图像指定资源 ID。

```
UINT m_uiLargeColdResID
```

## <a name="cmfctoolbarinfom_uilargedisabledresid"></a><a name="m_uilargedisabledresid"></a>CMFCToolBarInfo：m_uiLargeDisabledResID

为工具栏的所有大型禁用按钮图像指定资源 ID。

```
UINT m_uiLargeDisabledResID;
```

## <a name="cmfctoolbarinfom_uilargehotresid"></a><a name="m_uilargehotresid"></a>CMFCToolBarInfo：m_uiLargeHotResID

为工具栏的所有大型突出显示图像指定资源 ID。

```
UINT m_uiLargeHotResID;
```

## <a name="cmfctoolbarinfom_uimenudisabledresid"></a><a name="m_uimenudisabledresid"></a>CMFCToolBarinfo：m_uiMenuDisabledResID

为工具栏的命令不可用图像指定资源 ID。

```
UINT m_uiMenuDisabledResID;
```

## <a name="cmfctoolbarinfom_uimenuresid"></a><a name="m_uimenuresid"></a>CMFCToolBarinfo：m_uiMenuResID

为工具栏的所有常规菜单项图像指定资源 ID。

```
UINT m_uiMenuResID;
```

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)
