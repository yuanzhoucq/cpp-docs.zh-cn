---
title: CMFCRibbonQuickAccessToolBarDefaultState 类
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::AddCommand
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll
helpviewer_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CMFCRibbonQuickAccessToolBarDefaultState
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], AddCommand
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CopyFrom
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], RemoveAll
ms.assetid: eca99200-b87b-47ba-b2e8-2f3f2444b176
ms.openlocfilehash: eb6b36066f34036ae599a94f4d1c07b2c633e730
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753520"
---
# <a name="cmfcribbonquickaccesstoolbardefaultstate-class"></a>CMFCRibbonQuickAccessToolBarDefaultState 类

管理位于功能区栏[（CMFCRibbonBar 类](../../mfc/reference/cmfcribbonbar-class.md)）上的快速访问工具栏的默认状态的帮助器类。

## <a name="syntax"></a>语法

```
class CMFCRibbonQuickAccessToolBarDefaultState
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC 功能快速访问工具栏默认状态：：CMFC 功能快速访问工具栏默认状态](#cmfcribbonquickaccesstoolbardefaultstate)|构造 `CMFCRibbonQuickAccessToolbarDefaultState` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC 功能快速访问工具栏默认状态：：添加命令](#addcommand)|将命令添加到快速访问工具栏的默认状态。 这不会改变工具栏本身。|
|[CMFC 功能快速访问工具栏默认状态：：从](#copyfrom)|将一个快速访问工具栏的属性复制到另一个工具栏。|
|[CMFC 功能快速访问工具栏默认状态：：删除所有](#removeall)|从"快速访问工具栏"中删除所有命令。 这不会改变工具栏本身。|

## <a name="remarks"></a>备注

在应用程序中创建快速访问工具栏后，我们建议您通过调用[CMFC 功能区栏：：：设置快速访问默认状态](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate)来设置其默认状态。 当用户单击应用程序 **"选项"** 对话框的 **"自定义**"页上的 **"重置**"按钮时，将还原此默认状态。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CMFC 功能快速访问工具栏默认状态](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)

## <a name="example"></a>示例

下面的示例演示如何构造`CMFCRibbonQuickAccessToolbarDefaultState`类的对象以及如何将命令添加到快速访问工具栏的默认状态。

[!code-cpp[NVC_MFC_RibbonApp#21](../../mfc/reference/codesnippet/cpp/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]

## <a name="requirements"></a>要求

**标题：** afxribbon 快速访问工具栏.h

## <a name="cmfcribbonquickaccesstoolbardefaultstateaddcommand"></a><a name="addcommand"></a>CMFC 功能快速访问工具栏默认状态：：添加命令

将命令添加到快速访问工具栏的默认状态。

```cpp
void AddCommand(
    UINT uiCmd,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>参数

*[在] uiCmd*<br/>
指定命令 ID。

*[in] bIs 可见*<br/>
设置快速访问工具栏处于默认状态时命令的可见性。

### <a name="remarks"></a>备注

向 CMFC 功能删除快速访问工具默认状态添加命令可完成三个结果。 首先，每个添加的命令都列在快速访问工具栏右侧的下拉列表中。 通过这种方式，用户可以轻松地从"快速访问"工具栏中添加或删除该命令。 其次，将重置"快速访问工具栏"，以仅显示当用户单击 **"自定义"** 对话框中的 **"重置**"按钮时，在默认状态下列为可见的命令。 第三，如果您没有调用[CMFCRibbonBar：：SetQuickAccess命令](../../mfc/reference/cmfcribbonbar-class.md#setquickaccesscommands)，则快速访问工具栏使用此列表中的可见命令作为用户首次运行应用程序的默认可见命令。 添加所需的所有命令后，请致电[CMFCRibbonBar：：设置快速访问默认状态](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate)，以将此实例设置为该功能区栏的快速访问工具栏的默认状态。

## <a name="cmfcribbonquickaccesstoolbardefaultstatecopyfrom"></a><a name="copyfrom"></a>CMFC 功能快速访问工具栏默认状态：：从

将一个快速访问工具栏的属性复制到另一个工具栏。

```cpp
void CopyFrom(const CMFCRibbonQuickAccessToolBarDefaultState& src);
```

### <a name="parameters"></a>参数

*src*<br/>
[在]对要从中复制`CMFCRibbonQuickAccessToolBarDefaultState`的源对象的引用。

### <a name="remarks"></a>备注

此方法使用`CMFCRibbonQuickAccessToolBarDefaultState`[CMFCRibbonQuickAccessToolBarDefaultState：addCommand](#addcommand)方法将每个命令从源对象复制到此对象。

## <a name="cmfcribbonquickaccesstoolbardefaultstatecmfcribbonquickaccesstoolbardefaultstate"></a><a name="cmfcribbonquickaccesstoolbardefaultstate"></a>CMFC 功能快速访问工具栏默认状态：：CMFC 功能快速访问工具栏默认状态

构造快速访问工具栏默认状态对象。

```
CMFCRibbonQuickAccessToolBarDefaultState();
```

### <a name="remarks"></a>备注

默认情况下[，CMFRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)的新实例包含的命令列表为空。

## <a name="cmfcribbonquickaccesstoolbardefaultstateremoveall"></a><a name="removeall"></a>CMFC 功能快速访问工具栏默认状态：：删除所有

清除"快速访问工具栏"中的默认命令列表。

```cpp
void RemoveAll();
```

### <a name="remarks"></a>备注

此函数从此实例中删除以前调用[CMFC 功能障碍快速访问工具栏默认状态的所有命令：添加 AddCommand。](#addcommand)

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFC剪条类](../../mfc/reference/cmfcribbonbar-class.md)
