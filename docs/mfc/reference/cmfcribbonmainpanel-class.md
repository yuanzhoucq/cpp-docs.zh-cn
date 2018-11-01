---
title: CMFCRibbonMainPanel 类
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::Add
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddRecentFilesList
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToBottom
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToRight
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::GetCommandsFrame
helpviewer_keywords:
- CMFCRibbonMainPanel [MFC], Add
- CMFCRibbonMainPanel [MFC], AddRecentFilesList
- CMFCRibbonMainPanel [MFC], AddToBottom
- CMFCRibbonMainPanel [MFC], AddToRight
- CMFCRibbonMainPanel [MFC], GetCommandsFrame
ms.assetid: 1af78798-5e75-4365-9c81-a54aa5679602
ms.openlocfilehash: 101c718d25a2e06461156045deea5f42d85e2f4d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638212"
---
# <a name="cmfcribbonmainpanel-class"></a>CMFCRibbonMainPanel 类

实现在单击时显示的功能区面板[CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)。

## <a name="syntax"></a>语法

```
class CMFCRibbonMainPanel : public CMFCRibbonPanel
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|`CMFCRibbonMainPanel::CMFCRibbonMainPanel`|默认构造函数。|
|`CMFCRibbonMainPanel::~CMFCRibbonMainPanel`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCRibbonMainPanel::Add](#add)|将功能区元素添加到应用程序按钮面板的左窗格中。 (重写[cmfcribbonpanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add)。)|
|[CMFCRibbonMainPanel::AddRecentFilesList](#addrecentfileslist)|将文本字符串添加到新的文件列表菜单。|
|[CMFCRibbonMainPanel::AddToBottom](#addtobottom)|将功能区元素添加到功能区应用程序面板的底部窗格中。|
|[CMFCRibbonMainPanel::AddToRight](#addtoright)|将功能区元素添加到应用程序按钮面板的右窗格中。|
|`CMFCRibbonMainPanel::CreateObject`|由框架用于创建此类类型的动态实例。|
|[CMFCRibbonMainPanel::GetCommandsFrame](#getcommandsframe)|返回一个表示功能区的主面板的区域的矩形。|
|`CMFCRibbonMainPanel::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型相关联的对象。|

## <a name="remarks"></a>备注

框架显示`CMFCRibbonMainPanel`打开应用程序面板时。 它包含三个窗格：

- 左窗格中包含的文件，如关联的命令**开放**，**保存**，**打印**，以及**关闭**。 若要将命令添加到此窗格中，调用[CMFCRibbonMainPanel::Add](#add)。

- 在右窗格包含修改的左窗格中单击该命令的选项。 例如，如果您单击**另存为**从左窗格中，右窗格中可以显示可用的文件类型。 若要将项添加到此窗格中，调用[CMFCRibbonMainPanel::AddToRight](#addtoright)。

- 在底部窗格包含允许您更改应用程序的设置并退出程序的按钮。 若要将项添加到此窗格中，调用[CMFCRibbonMainPanel::AddToBottom](#addtobottom)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)

[CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)

## <a name="requirements"></a>要求

**标头：** afxRibbonMainPanel.h

##  <a name="add"></a>  CMFCRibbonMainPanel::Add

将功能区元素添加到应用程序按钮面板的左窗格中。

```
virtual void Add(CMFCRibbonBaseElement* pElem);
```

### <a name="parameters"></a>参数

*pElem*<br/>
[in、 out]指向要添加到主面板的功能区元素的指针。

### <a name="remarks"></a>备注

将功能区元素添加到面板。 使用此方法添加的元素将位于左侧列的主面板中。

##  <a name="addrecentfileslist"></a>  CMFCRibbonMainPanel::AddRecentFilesList

将文本字符串添加到新的文件列表菜单。

```
void AddRecentFilesList(
    LPCTSTR lpszLabel,
    int nWidth = 300);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
指定要添加到最近的文件列表的字符串。

*nWidth*<br/>
指定宽度，以像素为单位的最新的文件列表面板。

### <a name="remarks"></a>备注

##  <a name="addtobottom"></a>  CMFCRibbonMainPanel::AddToBottom

将功能区元素添加到功能区应用程序面板的底部窗格中。

```
void AddToBottom(CMFCRibbonMainPanelButton* pElem);
```

### <a name="parameters"></a>参数

*pElem*<br/>
[in、 out]指向要添加到主面板底部的功能区元素的指针。

### <a name="remarks"></a>备注

##  <a name="addtoright"></a>  CMFCRibbonMainPanel::AddToRight

将功能区元素添加到应用程序按钮面板的右窗格中。

```
void AddToRight(
    CMFCRibbonBaseElement* pElem,
    int nWidth = 300);
```

### <a name="parameters"></a>参数

*pElem*<br/>
指向要添加到主面板右侧的功能区元素的指针。

*nWidth*<br/>
指定宽度，以像素为单位的右侧面板。

### <a name="remarks"></a>备注

使用此函数将功能区元素添加到右侧面板。 在右侧面板通常会显示最近的文件列表，但您可以添加以下任何其他功能区元素。

##  <a name="getcommandsframe"></a>  CMFCRibbonMainPanel::GetCommandsFrame

返回一个表示功能区的主面板的区域的矩形。

```
CRect GetCommandsFrame() const;
```

### <a name="return-value"></a>返回值

一个表示功能区的主面板的区域的矩形。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel 类](../../mfc/reference/cmfcribbonpanel-class.md)
