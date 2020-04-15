---
title: CWaitCursor 类
ms.date: 11/04/2016
f1_keywords:
- CWaitCursor
- AFXWIN/CWaitCursor
- AFXWIN/CWaitCursor::CWaitCursor
- AFXWIN/CWaitCursor::Restore
helpviewer_keywords:
- CWaitCursor [MFC], CWaitCursor
- CWaitCursor [MFC], Restore
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
ms.openlocfilehash: 48ef8f9c965f54deafcc62451639f8c31021e900
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373181"
---
# <a name="cwaitcursor-class"></a>CWaitCursor 类

在单行中显示等待光标，在你执行较长操作时，此光标通常显示为一个沙漏。

## <a name="syntax"></a>语法

```
class CWaitCursor
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CWaitCursor：CWaitCursor](#cwaitcursor)|构造`CWaitCursor`对象并显示等待光标。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CWaitCursor：：恢复](#restore)|更改等待光标后还原它。|

## <a name="remarks"></a>备注

`CWaitCursor`没有基类。

良好的 Windows 编程实践要求，每当执行需要明显时间的操作时，都会显示等待光标。

要显示等待光标，只需在执行长时间`CWaitCursor`操作的代码之前定义变量。 对象的构造函数会自动显示等待光标。

当对象超出范围（在声明`CWaitCursor`对象的块的末尾）时，其析构函数将光标设置到前面的游标。 换句话说，对象会自动执行必要的清理。

> [!NOTE]
> 由于其构造函数和析构函数的工作方式，`CWaitCursor`对象始终声明为局部变量 - 它们永远不会声明为全局变量，也不会使用**new**分配。

如果执行可能导致光标更改的操作（如显示消息框或对话框），请调用[还原](#restore)成员函数以还原等待光标。 即使当前显示等待光标`Restore`，也可以调用。

显示等待光标的另一种方法是使用[CCmdTarget：：：开始等待光标](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)[，CmdTarget：：结束等待光标](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)，也许[CMdTarget：：还原等待光标](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)。 但是，`CWaitCursor`使用起来更容易，因为完成冗长的操作后，不需要将光标设置为上一个游标。

> [!NOTE]
> MFC 使用[CWinApp：:DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)虚拟函数设置和恢复光标。 您可以重写此函数以提供自定义行为。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CWaitCursor`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]

## <a name="cwaitcursorcwaitcursor"></a><a name="cwaitcursor"></a>CWaitCursor：CWaitCursor

要显示等待光标，只需在执行长时间`CWaitCursor`操作的代码之前声明对象。

```
CWaitCursor();
```

### <a name="remarks"></a>备注

构造函数会自动显示等待光标。

当对象超出范围（在声明`CWaitCursor`对象的块的末尾）时，其析构函数将光标设置到前面的游标。 换句话说，对象会自动执行必要的清理。

可以利用在块末尾调用析构函数（可能在函数末尾）这一事实，使等待光标仅在函数的一部分中处于活动状态。 此技术如下第二个示例所示。

> [!NOTE]
> 由于其构造函数和析构函数的工作方式，`CWaitCursor`对象始终声明为局部变量 - 它们永远不会声明为全局变量，也不会使用**新**分配 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]

## <a name="cwaitcursorrestore"></a><a name="restore"></a>CWaitCursor：：恢复

要还原等待游标，请在执行操作（如显示消息框或对话框）后调用此函数，这可能会将等待光标更改为另一个游标。

```
void Restore();
```

### <a name="remarks"></a>备注

即使当前显示等待光标`Restore`，也可以调用。

如果在声明`CWaitCursor`对象的函数以外的函数中需要还原等待游标，可以调用[CCmdTarget：：：还原WaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CMD目标：：开始等待光标](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)<br/>
[CmD目标：：结束等待光标](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)<br/>
[Cmd目标：：恢复等待光标](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)<br/>
[CWinApp：:Do等待光标](../../mfc/reference/cwinapp-class.md#dowaitcursor)<br/>
[如何操作：更改 Microsoft 基础类应用程序中的鼠标光标](https://go.microsoft.com/fwlink/p/?linkid=128044)
