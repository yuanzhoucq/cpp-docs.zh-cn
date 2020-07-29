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
ms.openlocfilehash: dfeedad18b3ebcefedff446699f074c86037a4a3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222870"
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
|[CWaitCursor::CWaitCursor](#cwaitcursor)|构造一个 `CWaitCursor` 对象并显示等待光标。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[CWaitCursor：： Restore](#restore)|在等待游标发生更改后将其还原。|

## <a name="remarks"></a>备注

`CWaitCursor`没有基类。

良好的 Windows 编程做法要求您每次执行耗时很长的操作时都显示一个等待光标。

若要显示等待光标，只需在 `CWaitCursor` 执行冗长操作的代码之前定义一个变量。 对象的构造函数会自动导致显示等待光标。

当对象超出范围时（在对象声明的块的结尾处 `CWaitCursor` ），其析构函数将游标设置为上一个游标。 换句话说，对象会自动执行必要的清理。

> [!NOTE]
> 由于对象的构造函数和析构函数的工作原理， `CWaitCursor` 始终将对象声明为局部变量，它们永远不会声明为全局变量，也不会将其分配给它们 **`new`** 。

如果执行的操作可能导致光标更改，如显示消息框或对话框，请调用[restore](#restore)成员函数来还原等待光标。 `Restore`即使当前显示的是等待游标，也可以调用。

显示等待光标的另一种方法是使用[CCmdTarget：： BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)、 [CCmdTarget：： EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)和[CCmdTarget：： RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)的组合。 但是， `CWaitCursor` 更易于使用，因为当完成长时间的操作时，无需将光标设置为上一个游标。

> [!NOTE]
> MFC 使用[CWinApp：:D owaitcursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)虚函数设置并还原游标。 您可以重写此函数以提供自定义行为。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CWaitCursor`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]

## <a name="cwaitcursorcwaitcursor"></a><a name="cwaitcursor"></a>CWaitCursor::CWaitCursor

若要显示等待光标，只需在 `CWaitCursor` 执行冗长操作的代码之前声明一个对象。

```
CWaitCursor();
```

### <a name="remarks"></a>备注

构造函数会自动导致显示等待光标。

当对象超出范围时（在对象声明的块的结尾处 `CWaitCursor` ），其析构函数将游标设置为上一个游标。 换句话说，对象会自动执行必要的清理。

您可以利用这一事实：在块的末尾（可能在函数的末尾之前）调用析构函数，使等待游标仅在函数的一部分中处于活动状态。 下面的第二个示例演示了此方法。

> [!NOTE]
> 由于对象的构造函数和析构函数的工作原理， `CWaitCursor` 始终将对象声明为局部变量，它们永远不会声明为全局变量，也不会分配给它们 **`new`** 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]

## <a name="cwaitcursorrestore"></a><a name="restore"></a>CWaitCursor：： Restore

若要还原等待游标，请在执行操作（如显示消息框或对话框）后调用此函数，这可能会将等待光标更改为另一个游标。

```cpp
void Restore();
```

### <a name="remarks"></a>备注

`Restore`即使当前显示等待光标也是一样的。

如果你需要在不是该对象声明的函数中还原等待游标 `CWaitCursor` ，则可以调用[CCmdTarget：： RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]

## <a name="see-also"></a>另请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget：： BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)<br/>
[CCmdTarget：： EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)<br/>
[CCmdTarget：： RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)<br/>
[CWinApp：:D oWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)<br/>
[如何实现：在 Microsoft 基础类应用程序中更改鼠标光标](https://go.microsoft.com/fwlink/p/?linkid=128044)
