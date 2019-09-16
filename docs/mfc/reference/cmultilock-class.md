---
title: CMultiLock 类
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
ms.openlocfilehash: b2fe3ecf2197b8edb13e89600b16e550deff9af2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504541"
---
# <a name="cmultilock-class"></a>CMultiLock 类

表示多线程程序中用于控制对多个资源的访问的访问控制机制。

## <a name="syntax"></a>语法

```
class CMultiLock
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMultiLock::CMultiLock](#cmultilock)|构造 `CMultiLock` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMultiLock::IsLocked](#islocked)|确定数组中的特定同步对象是否处于锁定状态。|
|[CMultiLock::Lock](#lock)|等待同步对象的数组。|
|[CMultiLock::Unlock](#unlock)|释放所有拥有的同步对象。|

## <a name="remarks"></a>备注

`CMultiLock`没有基类。

若要使用同步类[CSemaphore](../../mfc/reference/csemaphore-class.md)、 [CMutex](../../mfc/reference/cmutex-class.md)和[CEvent](../../mfc/reference/cevent-class.md)，可以创建一个`CMultiLock`或[CSingleLock](../../mfc/reference/csinglelock-class.md)对象，以等待并释放同步对象。 当`CMultiLock`有多个对象可以在特定时间使用时，请使用。 当`CSingleLock`只需等待一个对象时使用。

若要使用`CMultiLock`对象，请首先创建要等待的同步对象的数组。 接下来，在`CMultiLock`受控资源的类中的成员函数内调用对象的构造函数。 然后调用[锁定](#lock)成员函数来确定资源是否可用（已终止）。 如果一个为，则继续执行成员函数的其余部分。 如果没有可用的资源，请等待指定的资源释放一段时间，或返回失败。 完成资源的使用后，如果要再次使用该 `CMultiLock`对象 ，请调用 [Unlock](#unlock) 函数，或允许`CMultiLock`对象被销毁。

`CMultiLock`当线程有大量`CEvent`对象可以响应时，对象最有用。 创建一个包含所有指针的`CEvent`数组，然后调用`Lock`。 这将导致线程等待，直到其中一个事件发出信号。

有关如何使用`CMultiLock`对象的详细信息，请参阅[多线程处理：如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CMultiLock`

## <a name="requirements"></a>要求

**标头：** afxmt

##  <a name="cmultilock"></a>CMultiLock::CMultiLock

构造 `CMultiLock` 对象。

```
CMultiLock(
    CSyncObject* ppObjects [ ],
    DWORD dwCount,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>参数

*ppObjects*<br/>
指向要等待的同步对象的指针的数组。 不能为 NULL。

*dwCount*<br/>
*PpObjects*中的对象数。 必须大于 0。

*bInitialLock*<br/>
指定是否最初尝试访问任何提供的对象。

### <a name="remarks"></a>备注

创建要等待的同步对象数组后，将调用此函数。 它通常从必须等待某个同步对象变为可用的线程中调用。

##  <a name="islocked"></a>CMultiLock：： IsLocked

确定指定的对象是否为非终止（不可用）。

```
BOOL IsLocked(DWORD dwItem);
```

### <a name="parameters"></a>参数

*dwItem*<br/>
对象数组中对应于正在查询其状态的对象的索引。

### <a name="return-value"></a>返回值

如果指定的对象被锁定，则为非零值;否则为0。

##  <a name="lock"></a>  CMultiLock::Lock

调用此函数可获取对提供给`CMultiLock`构造函数的同步对象所控制的一个或多个资源的访问权限。

```
DWORD Lock(
    DWORD dwTimeOut = INFINITE,
    BOOL bWaitForAll = TRUE,
    DWORD dwWakeMask = 0);
```

### <a name="parameters"></a>参数

*dwTimeOut*<br/>
指定等待同步对象可用所需的时间（信号）。 如果是无限`Lock`的，将等待直到对象收到信号后才返回。

*bWaitForAll*<br/>
指定在返回前是否所有的对象都必须在同一时间终止。 如果为 FALSE `Lock` ，则当任何一个对象等待时，将返回。

*dwWakeMask*<br/>
指定允许中止等待的其他条件。 有关此参数的可用选项的完整列表，请参阅 Windows SDK 中的[MsgWaitForMultipleObjects](/windows/win32/api/winuser/nf-winuser-msgwaitformultipleobjects) 。

### <a name="return-value"></a>返回值

如果`Lock`失败，则返回-1。 如果成功，它将返回以下值之一：

- 介于 WAIT_OBJECT_0 和 WAIT_OBJECT_0 + 之间（对象数为-1）

   如果*bWaitForAll*为 TRUE，则所有对象均处于终止状态（可用）。 如果*bWaitForAll*为 FALSE，则返回值-WAIT_OBJECT_0 是对象的对象数组中的索引（可用）。

- WAIT_OBJECT_0 + （对象数量）

   在*dwWakeMask*中指定的事件在线程的输入队列中可用。

- 介于 WAIT_ABANDONED_0 和 WAIT_ABANDONED_0 + 之间（对象数为-1）

   如果*bWaitForAll*为 TRUE，则会向所有对象发出信号，并且至少有一个对象是被放弃的互斥体对象。 如果*bWaitForAll*为 FALSE，则返回值-WAIT_ABANDONED_0 为满足等待的被放弃的 mutex 对象的对象数组中的索引。

- WAIT_TIMEOUT

   *DwTimeOut*中指定的超时间隔已过期，无需等待。

### <a name="remarks"></a>备注

如果*bWaitForAll*为 TRUE， `Lock`则将在所有同步对象同时终止时立即返回。 如果*bWaitForAll*为 FALSE， `Lock`则将在一个或多个同步对象发出信号后立即返回。

如果`Lock`无法立即返回，它将在返回前等待的时间不超过*dwTimeOut*参数中指定的毫秒数。 如果*dwTimeOut*是无限的`Lock` ，将不会返回，直到获取了对对象的访问权限或满足*dwWakeMask*中指定的条件。 否则，如果`Lock`能够获取同步对象，则它将返回成功; 否则，将返回失败。

##  <a name="unlock"></a>  CMultiLock::Unlock

释放由拥有的`CMultiLock`同步对象。

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>参数

*lCount*<br/>
要释放的引用计数的数目。 必须大于 0。 如果指定的量会导致对象的计数超过其最大值，则不会更改计数，并且函数返回 FALSE。

*lPrevCount*<br/>
指向一个变量，用于接收同步对象的前一个计数。 如果为 NULL，则不返回前一个计数。

### <a name="return-value"></a>返回值

如果函数成功，则为非零值;否则为0。

### <a name="remarks"></a>备注

此函数由`CMultiLock`的析构函数调用。

第一种形式`Unlock`的尝试对`CMultiLock`管理的同步对象进行解锁。 的第二种`Unlock`形式尝试对所`CSemaphore`拥有`CMultiLock`的对象进行解锁。 如果`CMultiLock`不拥有任何锁定`CSemaphore`的对象，则该函数将返回 FALSE; 否则返回 TRUE。 *lCount*和*lpPrevCount*与[CSingleLock：： Unlock](../../mfc/reference/csinglelock-class.md#unlock)的参数完全相同。 的第二种`Unlock`形式很少适用于 multilock 情况。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)
