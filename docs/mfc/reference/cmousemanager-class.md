---
title: CMouseManager 类
ms.date: 11/04/2016
f1_keywords:
- CMouseManager
- AFXMOUSEMANAGER/CMouseManager
- AFXMOUSEMANAGER/CMouseManager::AddView
- AFXMOUSEMANAGER/CMouseManager::GetViewDblClickCommand
- AFXMOUSEMANAGER/CMouseManager::GetViewIconId
- AFXMOUSEMANAGER/CMouseManager::GetViewIdByName
- AFXMOUSEMANAGER/CMouseManager::GetViewNames
- AFXMOUSEMANAGER/CMouseManager::LoadState
- AFXMOUSEMANAGER/CMouseManager::SaveState
- AFXMOUSEMANAGER/CMouseManager::SetCommandForDblClk
helpviewer_keywords:
- CMouseManager [MFC], AddView
- CMouseManager [MFC], GetViewDblClickCommand
- CMouseManager [MFC], GetViewIconId
- CMouseManager [MFC], GetViewIdByName
- CMouseManager [MFC], GetViewNames
- CMouseManager [MFC], LoadState
- CMouseManager [MFC], SaveState
- CMouseManager [MFC], SetCommandForDblClk
ms.assetid: a4d05017-4e44-4a40-8b57-4ece0de20481
ms.openlocfilehash: d05a2e186f001a69310e99cec013193a4d1bff3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319726"
---
# <a name="cmousemanager-class"></a>CMouseManager 类

允许用户在用户双击该视图中时将不同的命令与特定的[CView](../../mfc/reference/cview-class.md)对象相关联。

## <a name="syntax"></a>语法

```
class CMouseManager : public CObject
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[鼠标管理器：：添加视图](#addview)|将`CView`对象添加到 **"自定义"** 对话框中。 "**自定义"** 对话框使用户能够将双击与每个列出的视图的命令相关联。|
|[鼠标管理器：：获取查看点击命令](#getviewdblclickcommand)|返回用户在提供的视图中双击时执行的命令。|
|[鼠标管理器：：获取视图图标](#getviewiconid)|返回与提供的视图 ID 关联的图标。|
|[鼠标管理器：获取查看 IdBY 名称](#getviewidbyname)|返回与提供的视图名称关联的视图 ID。|
|[鼠标管理器：：获取查看名称](#getviewnames)|检索所有添加的视图名称的列表。|
|[鼠标管理器：：加载状态](#loadstate)|从`CMouseManager`Windows 注册表加载状态。|
|[鼠标管理器：：保存状态](#savestate)|将`CMouseManager`状态写入 Windows 注册表。|
|[鼠标管理器：：SetCommandForBlClk](#setcommandfordblclk)|关联提供的命令和提供的视图。|

## <a name="remarks"></a>备注

类`CMouseManager`维护`CView`对象的集合。 每个视图都由名称和 ID 标识。 这些视图显示在 **"自定义"** 对话框中。 用户可以通过 **"自定义"** 对话框更改与任何视图关联的命令。 当用户双击该视图中时，将执行关联的命令。 要从编码角度支持这一点，您必须处理WM_LBUTTONDBLCLK消息，并在该`CView`对象的代码中调用[CWinAppEx：onViewDoubleClick](../../mfc/reference/cwinappex-class.md#onviewdoubleclick)函数。

不应手动创建`CMouseManager`对象。 它将由应用程序的框架创建。 当用户退出应用程序时，它也会自动销毁。 要获取指向应用程序的鼠标管理器的指针，请致电[CWinAppEx：：GetMouseManager](../../mfc/reference/cwinappex-class.md#getmousemanager)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CMouseManager`

## <a name="requirements"></a>要求

**标题：** afxmouse 管理器.h

## <a name="cmousemanageraddview"></a><a name="addview"></a>鼠标管理器：：添加视图

将[CView](../../mfc/reference/cview-class.md)对象注册到[CMouseManager 类](../../mfc/reference/cmousemanager-class.md)，以支持自定义鼠标行为。

```
BOOL AddView(
    int iViewId,
    UINT uiViewNameResId,
    UINT uiIconId = 0);

BOOL AddView(
    int iId,
    LPCTSTR lpszViewName,
    UINT uiIconId = 0);
```

### <a name="parameters"></a>参数

*iViewId*<br/>
[在]视图 ID。

*uiViewNameResId*<br/>
[在]引用视图名称的资源字符串 ID。

*乌伊科尼*<br/>
[在]视图图标 ID。

*Iid*<br/>
[在]视图 ID。

*lpszView名称*<br/>
[在]视图名称。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

为了支持自定义鼠标行为，必须向`CMouseManager`对象注册视图。 从`CView`类派生的任何对象都可以注册到鼠标管理器。 与视图关联的字符串和图标将显示在 **"自定义"** 对话框的 **"鼠标"** 选项卡中。

程序员有责任创建和维护视图 ID，如*iViewId*和*iId*。

有关如何提供自定义鼠标行为的详细信息，请参阅[键盘和鼠标自定义](../../mfc/keyboard-and-mouse-customization.md)。

### <a name="example"></a>示例

`CMouseManager`下面的示例演示如何使用`CWinAppEx::GetMouseManager``AddView``CMouseManager`类中的 方法和 方法检索指向对象的指针。 此代码段是[状态收集示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_StateCollection#4](../../mfc/reference/codesnippet/cpp/cmousemanager-class_1.cpp)]

## <a name="cmousemanagergetviewdblclickcommand"></a><a name="getviewdblclickcommand"></a>鼠标管理器：：获取查看点击命令

返回用户在提供的视图中双击时执行的命令。

```
UINT GetViewDblClickCommand(int iId) const;
```

### <a name="parameters"></a>参数

*Iid*<br/>
[在]视图 ID。

### <a name="return-value"></a>返回值

如果视图与命令关联，则命令标识符;否则 0。

## <a name="cmousemanagergetviewiconid"></a><a name="getviewiconid"></a>鼠标管理器：：获取视图图标

检索与视图 ID 关联的图标。

```
UINT GetViewIconId(int iViewId) const;
```

### <a name="parameters"></a>参数

*iViewId*<br/>
[在]视图 ID。

### <a name="return-value"></a>返回值

图标资源标识符（如果成功）;否则 0。

### <a name="remarks"></a>备注

如果视图不是首先使用[CMouseManager 注册，](#addview)则此方法将失败： ：addView 。

## <a name="cmousemanagergetviewidbyname"></a><a name="getviewidbyname"></a>鼠标管理器：获取查看 IdBY 名称

检索与视图名称关联的视图 ID。

```
int GetViewIdByName(LPCTSTR lpszName) const;
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
[在]视图名称。

### <a name="return-value"></a>返回值

视图 ID（如果成功）;否则 0。

### <a name="remarks"></a>备注

此方法搜索使用[CMouseManager 注册的视图：：addView](#addview)。

## <a name="cmousemanagergetviewnames"></a><a name="getviewnames"></a>鼠标管理器：：获取查看名称

检索所有已注册视图名称的列表。

```
void GetViewNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>参数

*名称列表*<br/>
[出]对`CStringList`对象的引用。

### <a name="remarks"></a>备注

此方法使用`listOfNames`[CMouseManager：：：AddView](#addview)注册的所有视图的名称填充参数。

## <a name="cmousemanagerloadstate"></a><a name="loadstate"></a>鼠标管理器：：加载状态

从注册表加载[CMouseManager 类](../../mfc/reference/cmousemanager-class.md)的状态。

```
BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>参数

*lpsz配置文件名称*<br/>
[在]注册表项的路径。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

从注册表加载的状态信息包括已注册的视图、视图标识符和关联的命令。 如果参数*lpszProfileName*为 NULL，则此`CMouseManager`函数将加载[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)控制的默认注册表位置的数据。

在大多数情况下，您不必直接调用此函数。 它称为工作区初始化过程的一部分。 有关工作区初始化过程的详细信息，请参阅[CWinAppEx：：LoadState](../../mfc/reference/cwinappex-class.md#loadstate)。

## <a name="cmousemanagersavestate"></a><a name="savestate"></a>鼠标管理器：：保存状态

将[CMouseManager 类](../../mfc/reference/cmousemanager-class.md)的状态写入注册表。

```
BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>参数

*lpsz配置文件名称*<br/>
[在]注册表项的路径。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

写入注册表的状态信息包括所有已注册的视图、视图标识符和关联的命令。 如果参数*lpszProfileName*为 NULL，则此`CMouseManager`函数将数据写入[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)控制的默认注册表位置。

在大多数情况下，您不必直接调用此函数。 它称为工作区序列化过程的一部分。 有关工作区序列化过程的详细信息，请参阅[CWinAppEx：：：保存状态](../../mfc/reference/cwinappex-class.md#savestate)。

## <a name="cmousemanagersetcommandfordblclk"></a><a name="setcommandfordblclk"></a>鼠标管理器：：SetCommandForBlClk

将自定义命令与首次向鼠标管理器注册的视图关联。

```
void SetCommandForDblClk(
    int iViewId,
    UINT uiCmd);
```

### <a name="parameters"></a>参数

*iViewId*<br/>
[在]视图标识符。

*乌伊Cmd*<br/>
[在]命令标识符。

### <a name="remarks"></a>备注

为了将自定义命令与视图关联，必须首先使用[CMouseManager：：：AddView](#addview)注册视图。 该方法`AddView`需要视图标识符作为输入参数。 注册视图后，可以使用提供给 的相同视图`CMouseManager::SetCommandForDblClk`标识符输入参数进行调用`AddView`。 此后，当用户双击已注册视图中的鼠标时，应用程序将执行*uiCmd*指示的命令。 要支持自定义鼠标行为，还需要自定义在鼠标管理器中注册的视图。 有关自定义鼠标行为的详细信息，请参阅[键盘和鼠标自定义](../keyboard-and-mouse-customization.md)。

如果*uiCmd*设置为 0，则指定的视图不再与命令关联。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)<br/>
[键盘和鼠标自定义](../../mfc/keyboard-and-mouse-customization.md)
