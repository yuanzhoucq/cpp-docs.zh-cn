---
title: CEvent 类
ms.date: 11/04/2016
f1_keywords:
- CEvent
- AFXMT/CEvent
- AFXMT/CEvent::CEvent
- AFXMT/CEvent::PulseEvent
- AFXMT/CEvent::ResetEvent
- AFXMT/CEvent::SetEvent
- AFXMT/CEvent::Unlock
helpviewer_keywords:
- CEvent [MFC], CEvent
- CEvent [MFC], PulseEvent
- CEvent [MFC], ResetEvent
- CEvent [MFC], SetEvent
- CEvent [MFC], Unlock
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
ms.openlocfilehash: 009a17342cb92025d67bf2fe0df1b9d5c7c0c6f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373962"
---
# <a name="cevent-class"></a>CEvent 类

表示事件，它是一个同步对象，使一个线程能够通知另一个线程发生了事件。

## <a name="syntax"></a>语法

```
class CEvent : public CSyncObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[活动：：CEvent](#cevent)|构造 `CEvent` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[活动：:Pulse事件](#pulseevent)|将事件设置为可用（信号），释放等待线程，并将事件设置为不可用（非信号）。|
|[活动：：重置事件](#resetevent)|将事件设置为不可用（非信号）。|
|[活动：：设置事件](#setevent)|将事件设置为可用（信号），并释放任何等待线程。|
|[活动：：解锁](#unlock)|释放事件对象。|

## <a name="remarks"></a>备注

当线程必须知道何时执行其任务时，事件很有用。 例如，当有新数据可用时，必须通知将数据复制到数据存档的线程。 通过使用`CEvent`对象在新数据可用时通知复制线程，线程可以尽快执行其任务。

`CEvent`对象有两种类型：手动和自动。

释放至少`CEvent`一个线程后，自动对象将自动返回到非信号（不可用）状态。 默认情况下，`CEvent`除非在构造期间传递`TRUE` *bManualReset*参数，否则对象是自动的。

手动`CEvent`对象将保持[SetEvent](#setevent)或[ResetEvent](#resetevent)设置的状态，直到调用其他函数。 要创建手动`CEvent`对象，请在`TRUE``bManualReset`构造期间传递参数。

要使用`CEvent`对象，`CEvent`在需要对象时构造该对象。 指定要等待的事件的名称，并指定应用程序最初应拥有它。 然后，当构造函数返回时，可以访问该事件。 调用[SetEvent](#setevent)以发出事件对象信号（使事件对象可用），然后在访问受控资源后调用["解锁](#unlock)"。

使用`CEvent`对象的替代方法是将类型的`CEvent`变量作为数据成员添加到要控制的类中。 在构造受控对象期间，调用`CEvent`数据成员的构造函数并指定事件最初是否发出信号，并指定所需的事件对象类型、事件的名称（如果它将跨进程边界使用）以及所需的任何安全属性。

要以这种方式访问`CEvent`由对象控制的资源，请首先在资源的访问方法中创建[CSingleLock](../../mfc/reference/csinglelock-class.md)类型的变量或[CMultiLock](../../mfc/reference/cmultilock-class.md)类型的变量。 然后调用锁`Lock`对象的方法（例如[，CMultiLock：：锁定](../../mfc/reference/cmultilock-class.md#lock)）。 此时，线程将获取对资源的访问，等待资源被释放并获取访问权限，或者等待资源释放、超时，并且无法访问资源。 在任何情况下，您的资源都以线程安全的方式访问。 要释放资源，请调用`SetEvent`事件对象信号，然后使用锁定对象`Unlock`的方法（例如[，CMultiLock：：解锁](../../mfc/reference/cmultilock-class.md#unlock)），或让锁定对象退出范围。

有关如何使用`CEvent`对象的详细信息，请参阅[多线程：如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]

[!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CEvent`

## <a name="requirements"></a>要求

**标题：** afxmt.h

## <a name="ceventcevent"></a><a name="cevent"></a>活动：：CEvent

构造命名或未命名`CEvent`的对象。

```
CEvent(
    BOOL bInitiallyOwn = FALSE,
    BOOL bManualReset = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>参数

*b 初始拥有*<br/>
如果为 TRUE，则启用`CMultilock``CSingleLock`或 对象的线程。 否则，所有想要访问资源的线程都必须等待。

*b手动重置*<br/>
如果 TRUE，则指定事件对象是手动事件，否则事件对象是自动事件。

*lpsz名称*<br/>
`CEvent` 对象的名称。 如果要跨进程边界使用该对象，则必须提供该对象。 如果名称与现有事件匹配，则构造函数将生成一个新`CEvent`对象，该对象引用该名称的事件。 如果名称与现有不是事件的同步对象匹配，则构造将失败。 如果为 NULL，则名称将为空。

*lpsa属性*<br/>
事件对象的安全属性。 有关此结构的完整说明，请参阅 Windows SDK 中的[SECURITY_ATTRIBUTES。](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))

### <a name="remarks"></a>备注

要访问或`CEvent`释放对象，请创建[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)对象，并调用其[锁定](../../mfc/reference/csinglelock-class.md#lock)和[解锁](../../mfc/reference/csinglelock-class.md#unlock)成员函数。

要将`CEvent`对象的状态更改为信号（线程不必等待），请调用[SetEvent](#setevent)或[PulseEvent](#pulseevent)。 要将`CEvent`对象的状态设置为非信号状态（线程必须等待），请调用[ResetEvent](#resetevent)。

> [!IMPORTANT]
> 创建对象后`CEvent`，请使用[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)确保互斥体不存在。 如果互斥体确实意外存在，则可能表示恶意进程正在蹲下，并且可能打算恶意使用互斥体。 在这种情况下，建议的安全意识过程是关闭句柄并继续，就像创建对象时失败一样。

## <a name="ceventpulseevent"></a><a name="pulseevent"></a>活动：:Pulse事件

将事件的状态设置为信号（可用），释放任何等待的线程，并自动将其重置为非信号（不可用）。

```
BOOL PulseEvent();
```

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0。

### <a name="remarks"></a>备注

如果事件是手动的，则释放所有等待线程，将事件设置为非信号，然后`PulseEvent`返回。 如果事件是自动的，则释放单个线程，将事件设置为非信号，然后`PulseEvent`返回。

如果没有线程等待，或者无法立即释放线程，则`PulseEvent`将事件的状态设置为非信号状态并返回。

`PulseEvent`使用基础 Win32`PulseEvent`函数，可以通过内核模式异步过程调用暂时从等待状态中删除该函数。 因此，`PulseEvent`不可靠，不应由新应用程序使用。 有关详细信息，请参阅[PulseEvent 函数](/windows/win32/api/winbase/nf-winbase-pulseevent)。

## <a name="ceventresetevent"></a><a name="resetevent"></a>活动：：重置事件

将事件的状态设置为非信号状态，直到[SetEvent](#setevent)成员函数显式设置为发出信号。

```
BOOL ResetEvent();
```

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0。

### <a name="remarks"></a>备注

这将导致希望访问此事件的所有线程等待。

自动事件不使用此成员函数。

## <a name="ceventsetevent"></a><a name="setevent"></a>活动：：设置事件

将事件的状态设置为信号，释放任何等待的线程。

```
BOOL SetEvent();
```

### <a name="return-value"></a>返回值

如果函数成功，则非零，否则为 0。

### <a name="remarks"></a>备注

如果事件是手动的，则事件将保持信号状态，直到调用[ResetEvent。](#resetevent) 在这种情况下，可以释放多个线程。 如果事件是自动的，则事件将保持信号状态，直到释放单个线程。 然后，系统会将事件的状态设置为非信号状态。 如果没有线程等待，则状态将保持信号状态，直到释放一个线程。

## <a name="ceventunlock"></a><a name="unlock"></a>活动：：解锁

释放事件对象。

```
BOOL Unlock();
```

### <a name="return-value"></a>返回值

如果线程拥有事件对象且事件是自动事件，则非零;否则 0。

### <a name="remarks"></a>备注

如果线程的锁对象要重用，则此成员函数由当前拥有自动事件的线程调用，以便在它们完成后释放它。 如果不重用锁对象，锁定对象的析构函数将调用此函数。

## <a name="see-also"></a>另请参阅

[CSync对象类](../../mfc/reference/csyncobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
