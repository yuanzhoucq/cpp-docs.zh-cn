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
ms.openlocfilehash: fbf2d834163199107aae44bd5723ceff79e36f91
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506681"
---
# <a name="cevent-class"></a>CEvent 类

表示一个事件, 该事件是一个同步对象, 允许一个线程通知另一个线程已发生事件。

## <a name="syntax"></a>语法

```
class CEvent : public CSyncObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CEvent::CEvent](#cevent)|构造 `CEvent` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CEvent::PulseEvent](#pulseevent)|将事件设置为可用 (已发出信号), 释放等待线程, 并将事件设置为不可用 (非终止)。|
|[CEvent::ResetEvent](#resetevent)|将事件设置为不可用 (非终止)。|
|[CEvent::SetEvent](#setevent)|将事件设置为可用 (已终止) 并释放任何等待线程。|
|[CEvent::Unlock](#unlock)|释放事件对象。|

## <a name="remarks"></a>备注

当线程必须知道何时执行其任务时, 事件很有用。 例如, 当新数据可用时, 将数据复制到数据存档的线程必须得到通知。 当新数据`CEvent`可用时, 通过使用对象通知复制线程, 该线程可以尽快执行其任务。

`CEvent`对象有两种类型: 手动和自动。

在至少`CEvent`一个线程释放后, 自动对象自动返回到非终止 (不可用) 状态。 默认情况下, `CEvent`对象是自动的, 除非`TRUE`在构造过程中传递*bManualReset*参数。

手动`CEvent`对象始终处于[SetEvent](#setevent)或[ResetEvent](#resetevent)设置的状态, 直到调用另一个函数。 若要创建手动`CEvent`对象, 请`TRUE`在构造`bManualReset`期间传递参数。

若要使用`CEvent`对象, 请在`CEvent`需要时构造对象。 指定要等待的事件的名称, 并指定应用程序最初应拥有该事件。 然后, 你可以在构造函数返回时访问事件。 调用[SetEvent](#setevent)可对事件对象进行信号处理, 然后在访问完受控资源后调用[Unlock](#unlock) 。

使用`CEvent`对象的一种替代方法是将类型`CEvent`的变量作为数据成员添加到要控制的类。 在构造受控对象的过程中, 调用`CEvent`数据成员的构造函数, 并指定该事件最初是否发出信号, 还可以指定所需的事件对象的 specifythe 类型, 事件的名称 (如果将跨进程使用)边界) 以及所需的任何安全属性。

若要以这种方式访问`CEvent`由对象控制的资源, 请首先在资源的访问方法中创建一个类型为[CSingleLock](../../mfc/reference/csinglelock-class.md)或[CMultiLock](../../mfc/reference/cmultilock-class.md)的变量。 然后调用`Lock` lock 对象的方法 (例如, [CMultiLock:: lock](../../mfc/reference/cmultilock-class.md#lock))。 此时, 你的线程将获取对资源的访问权限, 等待资源释放并获取访问权限, 或者等待资源释放、超时, 并无法访问资源。 在任何情况下, 都已以线程安全的方式访问了资源。 若要释放资源, 请`SetEvent`调用以通知事件对象, 然后`Unlock`使用 lock 对象的方法 (例如, [CMultiLock:: Unlock](../../mfc/reference/cmultilock-class.md#unlock)), 或让锁对象不在范围内。

有关如何使用`CEvent`对象的详细信息, 请参阅[多线程处理:如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]

[!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CEvent`

## <a name="requirements"></a>要求

**标头:** afxmt

##  <a name="cevent"></a>CEvent::CEvent

构造已命名或未`CEvent`命名的对象。

```
CEvent(
    BOOL bInitiallyOwn = FALSE,
    BOOL bManualReset = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>参数

*bInitiallyOwn*<br/>
如果为 TRUE, 则启用`CMultilock`或`CSingleLock`对象的线程。 否则, 所有要访问资源的线程必须等待。

*bManualReset*<br/>
如果为 TRUE, 则将事件对象指定为手动事件, 否则事件对象将为自动事件。

*lpszName*<br/>
`CEvent` 对象的名称。 如果对象将跨进程边界使用, 则必须提供。 如果该名称与现有事件匹配, 则构造函数将生成`CEvent`一个引用该名称的事件的新对象。 如果该名称与不是事件的现有同步对象匹配, 则构造将失败。 如果为 NULL, 则名称将为 null。

*lpsaAttribute*<br/>
事件对象的安全特性。 有关此结构的完整说明, 请参阅 Windows SDK 中的[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 。

### <a name="remarks"></a>备注

若要访问或释放`CEvent`对象, 请创建[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)对象, 并调用其[锁定](../../mfc/reference/csinglelock-class.md#lock)和[取消锁定](../../mfc/reference/csinglelock-class.md#unlock)成员函数。

若要将`CEvent`对象的状态更改为 "已终止" (线程无需等待), 请调用[SetEvent](#setevent)或[PulseEvent](#pulseevent)。 若要将`CEvent`对象的状态设置为非终止 (threads 必须等待), 请调用[ResetEvent](#resetevent)。

> [!IMPORTANT]
>  创建`CEvent`对象后, 请使用[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)确保互斥体不存在。 如果互斥体确实存在, 则可能表示未强占恶意进程, 并可能会有意使用该互斥体。 在这种情况下, 建议的安全意识过程是关闭句柄, 然后继续操作, 就像创建对象时出错一样。

##  <a name="pulseevent"></a>CEvent::P ulseEvent

将事件状态设置为 "已终止" (可用), 释放任何正在等待的线程, 并自动将其重置为非终止 (不可用)。

```
BOOL PulseEvent();
```

### <a name="return-value"></a>返回值

如果函数成功, 则为非零值;否则为0。

### <a name="remarks"></a>备注

如果事件为手动, 则释放所有正在等待的线程, 将事件设置为非终止, 并`PulseEvent`返回。 如果事件为自动, 则释放单个线程, 将事件设置为非终止, 并`PulseEvent`返回。

如果没有线程正在等待, 或不能立即释放任何线程, `PulseEvent`则会将事件的状态设置为非终止, 并返回。

`PulseEvent`使用基础 Win32 `PulseEvent`函数, 该函数可通过内核模式异步过程调用暂时从等待状态中移除。 因此, `PulseEvent`不可靠, 不应由新应用程序使用。 有关详细信息, 请参阅[PulseEvent 函数](/windows/win32/api/winbase/nf-winbase-pulseevent)。

##  <a name="resetevent"></a>CEvent::ResetEvent

将事件状态设置为非终止, 直到将其显式设置为[SetEvent](#setevent)成员函数发出的信号。

```
BOOL ResetEvent();
```

### <a name="return-value"></a>返回值

如果函数成功, 则为非零值;否则为0。

### <a name="remarks"></a>备注

这将导致所有等待访问此事件的线程等待。

此成员函数不由自动事件使用。

##  <a name="setevent"></a>CEvent:: SetEvent

将事件状态设置为 "已终止", 并释放任何等待的线程。

```
BOOL SetEvent();
```

### <a name="return-value"></a>返回值

如果函数成功, 则为非零; 否则为0。

### <a name="remarks"></a>备注

如果事件为手动, 则在调用[ResetEvent](#resetevent)之前, 该事件将保持发出信号。 在这种情况下, 可以释放多个线程。 如果事件为自动, 事件将一直保持终止状态, 直到一个线程被释放。 然后, 系统会将事件的状态设置为非终止。 如果没有等待的线程, 则状态将保持终止状态, 直到释放一个线程。

##  <a name="unlock"></a>CEvent:: Unlock

释放事件对象。

```
BOOL Unlock();
```

### <a name="return-value"></a>返回值

如果线程拥有事件对象并且事件为自动事件, 则为非零值;否则为0。

### <a name="remarks"></a>备注

此成员函数由当前拥有自动事件的线程调用, 以在完成操作后, 如果要重复使用其锁对象, 则调用该函数。 如果不重复使用锁对象, 则该函数将被锁对象的析构函数调用。

## <a name="see-also"></a>请参阅

[CSyncObject 类](../../mfc/reference/csyncobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
