---
title: CMFCRibbonQuickAccessToolBarDefaultState 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::AddCommand
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CMFCRibbonQuickAccessToolBarDefaultState
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], AddCommand
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CopyFrom
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], RemoveAll
ms.assetid: eca99200-b87b-47ba-b2e8-2f3f2444b176
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c7e237d5c1c7eb1eda792c6cbbc028960d851c07
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380355"
---
# <a name="cmfcribbonquickaccesstoolbardefaultstate-class"></a>CMFCRibbonQuickAccessToolBarDefaultState 类

默认状态管理器定位在功能区栏上的快速访问工具栏的帮助器类 ( [CMFCRibbonBar 类](../../mfc/reference/cmfcribbonbar-class.md))。

## <a name="syntax"></a>语法

```
class CMFCRibbonQuickAccessToolBarDefaultState
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState](#cmfcribbonquickaccesstoolbardefaultstate)|构造 `CMFCRibbonQuickAccessToolbarDefaultState` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)|将命令添加到默认状态的快速访问工具栏。 这不会更改该工具栏本身。|
|[CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom](#copyfrom)|将一个快速访问工具栏的属性复制到另一个。|
|[CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll](#removeall)|从快速访问工具栏中删除所有命令。 这不会更改该工具栏本身。|

## <a name="remarks"></a>备注

在应用程序中创建快速访问工具栏之后，我们建议您通过调用设置其默认状态[CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate)。 当用户单击还原此默认状态**重置**按钮**自定义**在应用程序页**选项**对话框。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CMFCRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)

## <a name="example"></a>示例

下面的示例演示如何构造的对象`CMFCRibbonQuickAccessToolbarDefaultState`类以及如何快速访问工具栏命令添加到默认状态。

[!code-cpp[NVC_MFC_RibbonApp#21](../../mfc/reference/codesnippet/cpp/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]

## <a name="requirements"></a>要求

**标头：** afxribbonquickaccesstoolbar.h

##  <a name="addcommand"></a>  CMFCRibbonQuickAccessToolBarDefaultState::AddCommand

将命令添加到默认状态的快速访问工具栏。

```
void AddCommand(
    UINT uiCmd,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>参数

*[] in uiCmd*<br/>
指定命令 id。

*[] in bIsVisible*<br/>
快速访问工具栏处于默认状态时，请设置命令的可见性。

### <a name="remarks"></a>备注

将命令添加到 CMFCRibbonQuickAccessToolBarDefaultState 完成三个结果。 首先，在快速访问工具栏右侧下拉列表中列出每个添加的命令。 以这种方式，用户可以轻松地添加或移除快速访问工具栏的命令。 其次，重置快速访问工具栏只列出了这些命令相同的可见性中的默认状态时显示在用户单击**重置**按钮**自定义**对话框。 第三，如果您不调用[CMFCRibbonBar::SetQuickAccessCommands](../../mfc/reference/cmfcribbonbar-class.md#setquickaccesscommands)，快速访问工具栏使用此列表中的可见命令作为默认可见命令的用户运行你的应用程序第一次。 添加所需的所有命令后，调用[CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate)要快速访问工具栏的功能区栏的此实例设置为默认状态。

##  <a name="copyfrom"></a>  CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom

将一个快速访问工具栏的属性复制到另一个。

```
void CopyFrom(const CMFCRibbonQuickAccessToolBarDefaultState& src);
```

### <a name="parameters"></a>参数

*src*<br/>
[in]对源的引用`CMFCRibbonQuickAccessToolBarDefaultState`要从复制对象。

### <a name="remarks"></a>备注

此方法将每个命令复制从源`CMFCRibbonQuickAccessToolBarDefaultState`对象的使用对象[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)方法。

##  <a name="cmfcribbonquickaccesstoolbardefaultstate"></a>  CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState

构造的快速访问工具栏默认状态对象。

```
CMFCRibbonQuickAccessToolBarDefaultState();
```

### <a name="remarks"></a>备注

默认情况下的列表命令的新实例[CMFRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)包含为空。

##  <a name="removeall"></a>  CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll

清除的快速访问工具栏中的默认命令的列表。

```
void RemoveAll();
```

### <a name="remarks"></a>备注

此函数从此实例的所有命令都中的上一个调用[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)添加。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBar 类](../../mfc/reference/cmfcribbonbar-class.md)
