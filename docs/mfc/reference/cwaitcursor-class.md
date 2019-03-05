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
ms.openlocfilehash: 7ce81e62ec6498ad84349108b4c4a07090b17de5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287121"
---
# <a name="cwaitcursor-class"></a>CWaitCursor 类

在单行中显示等待光标，在你执行较长操作时，此光标通常显示为一个沙漏。

## <a name="syntax"></a>语法

```
class CWaitCursor
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CWaitCursor::CWaitCursor](#cwaitcursor)|构造`CWaitCursor`对象，并显示等待光标。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CWaitCursor::Restore](#restore)|已更改后，将还原将等待光标。|

## <a name="remarks"></a>备注

`CWaitCursor` 没有基类。

很好的 Windows 编程实践要求时要执行的操作需要很长时间显示等待光标。

若要显示等待光标，只需定义`CWaitCursor`变量之前执行耗时较长的操作的代码。 对象的构造函数会自动导致将显示等待光标。

当对象超出范围 (在其中的块的末尾`CWaitCursor`声明对象)，其析构函数将光标设置到上一个游标。 换而言之，则对象将自动执行必要收尾工作。

> [!NOTE]
>  由于其构造函数和析构函数的工作原理`CWaitCursor`对象总是声明本地变量为 — 它们永远不会声明为全局变量，也不它们使用分配**新**。

如果执行一个操作，它可能会导致更改，例如，显示消息框或对话框中，调用的光标[还原](#restore)成员函数以还原将等待光标。 可以调用`Restore`甚至等待光标当前显示时。

若要显示等待光标的另一种方法是使用的组合[CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)， [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)，但也可能[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor). 但是，`CWaitCursor`易于使用，因为无需时较长的操作完成后，光标设置为上一个游标。

> [!NOTE]
>  MFC 设置并还原游标使用[CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)虚函数。 您可以重写此函数可提供自定义行为。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CWaitCursor`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]

##  <a name="cwaitcursor"></a>  CWaitCursor::CWaitCursor

若要显示等待光标，只需声明`CWaitCursor`对象之前执行耗时较长的操作的代码。

```
CWaitCursor();
```

### <a name="remarks"></a>备注

构造函数会自动导致将显示等待光标。

当对象超出范围 (在其中的块的末尾`CWaitCursor`声明对象)，其析构函数将光标设置到上一个游标。 换而言之，则对象将自动执行必要收尾工作。

您可以利用这一事实，析构函数调用 （这可能是在函数末尾之前） 的块的末尾部分函数使等待光标处于活动状态。 这种方法是在下面的第二个示例所示。

> [!NOTE]
>  由于其构造函数和析构函数的工作原理`CWaitCursor`对象总是声明本地变量为 — 它们永远不会声明全局变量，也不它们使用分配**新**。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]

##  <a name="restore"></a>  CWaitCursor::Restore

若要还原将等待光标，请在执行操作，例如显示消息框或对话框中，可能会将等待光标更改为另一个游标之后调用此函数。

```
void Restore();
```

### <a name="remarks"></a>备注

它是确定以调用`Restore`甚至时将等待光标当前显示。

如果需要还原在函数中不是在其中将等待光标`CWaitCursor`声明对象，您可以调用[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)<br/>
[CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)<br/>
[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)<br/>
[CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)<br/>
[如何实现:更改鼠标光标的 Microsoft 基础类应用程序中](http://go.microsoft.com/fwlink/p/?linkid=128044)
