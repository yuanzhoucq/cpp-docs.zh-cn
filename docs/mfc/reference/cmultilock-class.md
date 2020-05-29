---
title: C 多锁类
ms.date: 11/04/2016
f1_keywords:
- CMultiLock
- AFXMT/CMultiLock
- AFXMT/CMultiLock::CMultiLock
- AFXMT/CMultiLock::IsLocked
- AFXMT/CMultiLock::Lock
- AFXMT/CMultiLock::Unlock
helpviewer_keywords:
- CMultiLock [MFC], CMultiLock
- CMultiLock [MFC], IsLocked
- CMultiLock [MFC], Lock
- CMultiLock [MFC], Unlock
ms.assetid: c5b7c78b-1f81-4387-b7dd-2c813c5b6b61
ms.openlocfilehash: a051c6a510c53ac0c7c0a6efd8b4b5720080b264
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319716"
---
# <a name="cmultilock-class"></a>C 多锁类

表示多线程程序中用于控制对多个资源的访问的访问控制机制。

## <a name="syntax"></a>语法

```
class CMultiLock
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C 多重锁定：C 多重锁](#cmultilock)|构造 `CMultiLock` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C 多重锁定：锁定](#islocked)|确定阵列中的特定同步对象是否锁定。|
|[C 多重锁定：锁定](#lock)|等待同步对象的数组。|
|[C 多重锁定：解锁](#unlock)|释放任何拥有的同步对象。|

## <a name="remarks"></a>备注

`CMultiLock`没有基类。

要使用同步类[CSemaphore、CMutex](../../mfc/reference/csemaphore-class.md)和[CEvent](../../mfc/reference/cevent-class.md)，您可以创建一个`CMultiLock`或[CSingleLock](../../mfc/reference/csinglelock-class.md)对象来等待并释放同步对象。 [CMutex](../../mfc/reference/cmutex-class.md) `CMultiLock`当在特定时间可以使用多个对象时使用。 在`CSingleLock`一次只需等待一个对象时使用。

要使用对象`CMultiLock`，请先创建要等待的同步对象的数组。 接下来，在`CMultiLock`受控资源类中的成员函数内调用对象的构造函数。 然后调用[Lock](#lock)成员函数以确定资源是否可用（信号）。 如果是，请继续执行成员函数的其余部分。 如果没有可用资源，请等待指定的时间释放资源，或返回失败。 资源使用完成后，如果要再次使用该对象，[Unlock](#unlock)`CMultiLock`则调用 Unlock 函数，或者允许销毁`CMultiLock`该对象。

`CMultiLock`当线程具有大量可以响应`CEvent`的对象时，对象最有用。 创建包含所有指针的`CEvent`数组，并调用`Lock`。 这将导致线程等待，直到其中一个事件发出信号。

有关如何使用`CMultiLock`对象的详细信息，请参阅"[多线程：如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)"一文。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CMultiLock`

## <a name="requirements"></a>要求

**标题：** afxmt.h

## <a name="cmultilockcmultilock"></a><a name="cmultilock"></a>C 多重锁定：C 多重锁

构造 `CMultiLock` 对象。

```
CMultiLock(
    CSyncObject* ppObjects [ ],
    DWORD dwCount,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>参数

*ppObjects*<br/>
指向要等待的同步对象的指针数组。 不能为 NULL。

*dwCount*<br/>
*ppObjects*中的对象数。 必须大于 0。

*b 初始锁定*<br/>
指定是否最初尝试访问任何提供的对象。

### <a name="remarks"></a>备注

在创建要等待的同步对象数组后调用此函数。 它通常从线程内调用，线程必须等待其中一个同步对象变为可用。

## <a name="cmultilockislocked"></a><a name="islocked"></a>C 多重锁定：锁定

确定指定对象是否非信号（不可用）。

```
BOOL IsLocked(DWORD dwItem);
```

### <a name="parameters"></a>参数

*dwItem*<br/>
与正在查询其状态的对象对应的对象数组中的索引。

### <a name="return-value"></a>返回值

如果指定对象被锁定，则非零;否则 0。

## <a name="cmultilocklock"></a><a name="lock"></a>C 多重锁定：锁定

调用此函数以访问由提供给`CMultiLock`构造函数的同步对象控制的一个或多个资源。

```
DWORD Lock(
    DWORD dwTimeOut = INFINITE,
    BOOL bWaitForAll = TRUE,
    DWORD dwWakeMask = 0);
```

### <a name="parameters"></a>参数

*dwTimeOut*<br/>
指定等待同步对象可用（信号）的时间量。 如果 INFINITE，`Lock`将等待对象发出信号后再返回。

*bWaitForall*<br/>
指定是否等待的所有对象必须同时发出信号才能返回。 如果 FALSE，`Lock`将在等待的任何对象发出信号时返回。

*dwWakeMask*<br/>
指定允许中止等待的其他条件。 有关此参数的可用选项的完整列表，请参阅 Windows SDK 中的[MsgWaitForMulti 对象](/windows/win32/api/winuser/nf-winuser-msgwaitformultipleobjects)。

### <a name="return-value"></a>返回值

如果`Lock`失败，它将返回 - 1。 如果成功，它将返回以下值之一：

- 介于WAIT_OBJECT_0和WAIT_OBJECT_0 + 之间（对象数 - 1）

   如果*bWaitForAll*为 TRUE，则所有对象都发出信号（可用）。 如果*bWaitForAll*为 FALSE，则返回值 - WAIT_OBJECT_0是发出信号（可用）的对象数组中的索引。

- WAIT_OBJECT_0 = （对象数）

   在*dwWakeMask*中指定的事件在线程的输入队列中可用。

- 介于WAIT_ABANDONED_0和WAIT_ABANDONED_0之间 = （对象数 - 1）

   如果*bWaitForAll*为 TRUE，则所有对象都发出信号，并且至少有一个对象是废弃的互斥体。 如果*bWaitForAll*是 FALSE，则返回值 - WAIT_ABANDONED_0是满足等待的废弃互斥体对象数组中的索引。

- WAIT_TIMEOUT

   *在 dwTimeOut*中指定的超时间隔已过期，等待时间未成功。

### <a name="remarks"></a>备注

如果*bWaitForAll*为`Lock`TRUE，则一旦所有同步对象同时发出信号，将立即成功返回。 如果*bWaitForAll*为`Lock`FALSE，则一旦一个或多个同步对象发出信号，将立即返回。

如果`Lock`无法立即返回，它将等待不超过*dwTimeOut*参数中指定的毫秒数，然后再返回。 如果*dwTimeOut*是`Lock`INFINITE，则在获得对对象的访问权限或满足*dwWakeMask*中指定的条件之前，不会返回。 否则，如果`Lock`能够获取同步对象，它将成功返回;否则，它将成功返回。如果不是，它将返回失败。

## <a name="cmultilockunlock"></a><a name="unlock"></a>C 多重锁定：解锁

释放 拥有的`CMultiLock`同步对象。

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>参数

*lCount*<br/>
要释放的引用计数数。 必须大于 0。 如果指定量将导致对象的计数超过其最大值，则计数不会更改，并且函数将返回 FALSE。

*lPrevCount*<br/>
指向变量以接收同步对象的上一个计数。 如果为 NULL，则不返回以前的计数。

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0。

### <a name="remarks"></a>备注

此函数由`CMultiLock`析构函数调用。

`Unlock`尝试解锁 由`CMultiLock`管理的同步对象的第一种形式。 尝试解锁 拥有`Unlock``CSemaphore``CMultiLock`的对象的第二种形式。 如果没有`CMultiLock`任何锁定`CSemaphore`的对象，函数将返回 FALSE;如果函数不具有"FALSE"功能。否则，它将返回 TRUE。 *lCount*和*lpPrevCount*与[CSingleLock 的参数完全相同：：解锁](../../mfc/reference/csinglelock-class.md#unlock)。 第二种形式`Unlock`很少适用于多锁情况。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)
