---
title: CMFC功能主面板类
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
ms.openlocfilehash: 0fd1cd2fec31f9da0c2bec36d08586780f4f95c3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753577"
---
# <a name="cmfcribbonmainpanel-class"></a>CMFC功能主面板类

实现一个功能区面板，当您单击[CMFC 功能应用程序按钮](../../mfc/reference/cmfcribbonapplicationbutton-class.md)时显示。

## <a name="syntax"></a>语法

```
class CMFCRibbonMainPanel : public CMFCRibbonPanel
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`CMFCRibbonMainPanel::CMFCRibbonMainPanel`|默认构造函数。|
|`CMFCRibbonMainPanel::~CMFCRibbonMainPanel`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC功能中心面板：添加](#add)|将功能区元素添加到应用程序按钮面板的左侧窗格中。 （覆盖[CMFC 功能面板：：添加](../../mfc/reference/cmfcribbonpanel-class.md#add).）|
|[CMFC 功能中心面板：：添加最新文件列表](#addrecentfileslist)|将文本字符串添加到最近的文件列表菜单。|
|[CMFC 剪彩主面板：：添加](#addtobottom)|将功能区元素添加到功能区应用程序面板的底部窗格中。|
|[CMFC 功能主面板：：添加右侧](#addtoright)|将功能区元素添加到应用程序按钮面板的右侧窗格中。|
|`CMFCRibbonMainPanel::CreateObject`|由框架用于创建此类类型的动态实例。|
|[CMFC 功能主机面板：：获取命令框架](#getcommandsframe)|返回表示功能区主面板区域的矩形。|
|`CMFCRibbonMainPanel::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|

## <a name="remarks"></a>备注

框架显示打开应用程序`CMFCRibbonMainPanel`面板时的 。 它包含三个窗格：

- 左侧窗格包含与文件关联的命令，如 **"打开**"、**保存**、**打印**和**关闭**。 要向此窗格添加命令，请致电[CMFCRibbonMainPanel：：：添加](#add)。

- 右侧窗格包含修改在左侧窗格中单击的命令的选项。 例如，如果从左侧窗格单击 **"保存为"，** 则右侧窗格可以显示可用的文件类型。 要将项目添加到此窗格，请致电[CMFC 功能区主面板：：添加右](#addtoright)。

- 底部窗格包含允许您更改应用程序设置并退出程序的按钮。 要将项目添加到此窗格，请致电[CMFC 功能区主面板：：添加到底部](#addtobottom)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)

[CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)

## <a name="requirements"></a>要求

**标题：** afxRibbonMainPanel.h

## <a name="cmfcribbonmainpaneladd"></a><a name="add"></a>CMFC功能中心面板：添加

将功能区元素添加到应用程序按钮面板的左侧窗格中。

```
virtual void Add(CMFCRibbonBaseElement* pElem);
```

### <a name="parameters"></a>参数

*佩莱姆*<br/>
[进出]指向要添加到主面板的功能区元素的指针。

### <a name="remarks"></a>备注

向面板添加功能区元素。 使用此方法添加的元素将位于主面板的左列中。

## <a name="cmfcribbonmainpaneladdrecentfileslist"></a><a name="addrecentfileslist"></a>CMFC 功能中心面板：：添加最新文件列表

将文本字符串添加到最近的文件列表菜单。

```cpp
void AddRecentFilesList(
    LPCTSTR lpszLabel,
    int nWidth = 300);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
指定要添加到最近文件列表的字符串。

*n 宽度*<br/>
指定最近文件列表面板的宽度（以像素为单位）。

### <a name="remarks"></a>备注

## <a name="cmfcribbonmainpaneladdtobottom"></a><a name="addtobottom"></a>CMFC 剪彩主面板：：添加

将功能区元素添加到功能区应用程序面板的底部窗格中。

```cpp
void AddToBottom(CMFCRibbonMainPanelButton* pElem);
```

### <a name="parameters"></a>参数

*佩莱姆*<br/>
[进出]指向功能区元素的指针，用于添加到主面板的底部。

### <a name="remarks"></a>备注

## <a name="cmfcribbonmainpaneladdtoright"></a><a name="addtoright"></a>CMFC 功能主面板：：添加右侧

将功能区元素添加到应用程序按钮面板的右侧窗格中。

```cpp
void AddToRight(
    CMFCRibbonBaseElement* pElem,
    int nWidth = 300);
```

### <a name="parameters"></a>参数

*佩莱姆*<br/>
指向要添加到主面板右侧的功能区元素的指针。

*n 宽度*<br/>
指定右侧面板的宽度（以像素为单位）。

### <a name="remarks"></a>备注

使用此函数向右侧面板添加功能区元素。 右侧面板通常显示最近的文件列表，但您可以在此处添加任何其他功能区元素。

## <a name="cmfcribbonmainpanelgetcommandsframe"></a><a name="getcommandsframe"></a>CMFC 功能主机面板：：获取命令框架

返回表示功能区主面板区域的矩形。

```
CRect GetCommandsFrame() const;
```

### <a name="return-value"></a>返回值

表示功能区主面板区域的矩形。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel 类](../../mfc/reference/cmfcribbonpanel-class.md)
