---
title: CMFCTabTool提示信息结构
ms.date: 11/04/2016
f1_keywords:
- CMFCTabToolTipInfo
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
ms.openlocfilehash: a507d1e69b3524074e50fde0e87fc5ebb6e5ca03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367345"
---
# <a name="cmfctabtooltipinfo-structure"></a>CMFCTabTool提示信息结构

此结构提供有关用户悬停的 MDI 选项卡的信息。

## <a name="syntax"></a>语法

```
struct CMFCTabToolTipInfo
```

## <a name="members"></a>成员

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|[CMFCTabTool提示信息：：m_nTabIndex](#m_ntabindex)|指定选项卡控件的索引。|
|[CMFCTabTool提示信息：：m_pTabWnd](#m_ptabwnd)|指向选项卡控件的指针。|
|[CMFCTabTool提示信息：：m_strText](#m_strtext)|工具提示文本。|

## <a name="remarks"></a>备注

指向结构的`CMFCTabToolTipInfo`指针作为AFX_WM_ON_GET_TAB_TOOLTIP消息的参数传递。 启用 MDI 选项卡且用户悬停在选项卡控件上时，将生成此消息。

## <a name="example"></a>示例

下面的示例显示了如何在`CMFCTabToolTipInfo` [MDITabsDemo 示例中使用：MFC 选项卡式 MDI 应用程序](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)

## <a name="requirements"></a>要求

**标头：** afxbasetabctrl.h

## <a name="cmfctabtooltipinfom_ntabindex"></a><a name="m_ntabindex"></a>CMFCTabTool提示信息：：m_nTabIndex

指定选项卡控件的索引。

```
int m_nTabIndex;
```

### <a name="remarks"></a>备注

用户悬停在其中的选项卡的索引。

### <a name="example"></a>示例

下面的示例显示了如何在`m_nTabIndex` [MDITabsDemo 示例中使用：MFC 选项卡式 MDI 应用程序](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="cmfctabtooltipinfom_ptabwnd"></a><a name="m_ptabwnd"></a>CMFCTabTool提示信息：：m_pTabWnd

指向选项卡控件的指针。

```
CMFCBaseTabCtrl* m_pTabWnd;
```

### <a name="example"></a>示例

下面的示例显示了如何在`m_pTabWnd` [MDITabsDemo 示例中使用：MFC 选项卡式 MDI 应用程序](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="cmfctabtooltipinfom_strtext"></a><a name="m_strtext"></a>CMFCTabTool提示信息：：m_strText

工具提示文本。

```
CString m_strText;
```

### <a name="remarks"></a>备注

如果字符串为空，则不显示工具提示。

### <a name="example"></a>示例

下面的示例显示了如何在`m_strText` [MDITabsDemo 示例中使用：MFC 选项卡式 MDI 应用程序](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
