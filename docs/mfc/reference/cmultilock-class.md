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
ms.openlocfilehash: 107ed227c5515cbf2fcb08e957a64a4a17d8287a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57288652"
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
|[CMultiLock::IsLocked](#islocked)|确定是否数组中的特定的同步对象将被锁定。|
|[CMultiLock::Lock](#lock)|等待同步对象的数组。|
|[CMultiLock::Unlock](#unlock)|释放任何拥有的同步对象。|

## <a name="remarks"></a>备注

`CMultiLock` 没有基类。

若要使用同步类[CSemaphore](../../mfc/reference/csemaphore-class.md)， [CMutex](../../mfc/reference/cmutex-class.md)，并[CEvent](../../mfc/reference/cevent-class.md)，可以创建`CMultiLock`或[CSingleLock](../../mfc/reference/csinglelock-class.md)对象等待，并释放同步对象。 使用`CMultiLock`时可以使用在特定时间的多个对象。 使用`CSingleLock`时只需等待上一个对象，一次。

若要使用`CMultiLock`对象，请首先创建一个你想要等待同步对象数组。 接下来，调用`CMultiLock`受控的资源的类中的成员函数内的对象的构造函数。 然后调用[锁](#lock)成员函数以确定资源是否可用 （发出信号）。 如果是，继续使用成员函数的其余部分。 如果没有资源可用，等待指定的要释放的资源的时间内，或返回失败。 使用的资源完成后，调用[解锁](#unlock)函数如果`CMultiLock`对象将再次，使用或允许`CMultiLock`要销毁对象。

`CMultiLock` 对象是最有用，当线程必须大量`CEvent`对象可以响应。 创建一个数组，包含所有`CEvent`指针，并调用`Lock`。 这会导致线程等待，直到其中一个事件发出信号。

有关如何使用的详细信息`CMultiLock`对象，请参阅文章[多线程处理：如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CMultiLock`

## <a name="requirements"></a>要求

**标头：** afxmt.h

##  <a name="cmultilock"></a>  CMultiLock::CMultiLock

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
中的对象数*ppObjects*。 必须大于 0。

*bInitialLock*<br/>
指定是否以最初尝试访问的任何提供的对象。

### <a name="remarks"></a>备注

创建要等待的同步对象的数组后调用此函数。 它通常称为从内的线程必须等待的其中一个同步对象变得可用。

##  <a name="islocked"></a>  CMultiLock::IsLocked

确定指定的对象是否为非终止 （不可用）。

```
BOOL IsLocked(DWORD dwItem);
```

### <a name="parameters"></a>参数

*dwItem*<br/>
要查询其状态的对象所对应的对象的数组中的索引。

### <a name="return-value"></a>返回值

如果指定的对象被锁定，则非零值否则为 0。

##  <a name="lock"></a>  CMultiLock::Lock

调用此函数可获取对一个或多个由提供给的同步对象控制的资源访问权限`CMultiLock`构造函数。

```
DWORD Lock(
    DWORD dwTimeOut = INFINITE,
    BOOL bWaitForAll = TRUE,
    DWORD dwWakeMask = 0);
```

### <a name="parameters"></a>参数

*dwTimeOut*<br/>
指定的时间来等待同步对象可用 （发出信号）。 如果无限期，`Lock`将等待，直到对象返回之前发出信号。

*bWaitForAll*<br/>
指定是否必须在同一时间在返回之前收到信号等待的所有对象。 如果为 FALSE，`Lock`等待的对象之一发出的信号时，将返回。

*dwWakeMask*<br/>
指定允许中止在等待其他条件。 此参数的可用选项的完整列表，请参阅[MsgWaitForMultipleObjects](/windows/desktop/api/winuser/nf-winuser-msgwaitformultipleobjects) Windows SDK 中。

### <a name="return-value"></a>返回值

如果`Lock`失败，则返回-1。 如果成功，则返回以下值之一：

- WAIT_OBJECT_0 和 WAIT_OBJECT_0 + （多个对象-1） 之间

   如果*bWaitForAll*为 TRUE 时，所有对象都已都终止 （可用）。 如果*bWaitForAll*是 FALSE，则返回值-WAIT_OBJECT_0 是中的对象发出信号 （可用） 的对象的数组索引。

- WAIT_OBJECT_0 + （的对象数）

   中指定的事件*dwWakeMask*是线程的输入队列中可用。

- WAIT_ABANDONED_0 和 WAIT_ABANDONED_0 + （多个对象-1） 之间

   如果*bWaitForAll*为 TRUE，所有对象都已都终止，并且至少一个对象是一个放弃的互斥体对象。 如果*bWaitForAll*是 FALSE，则返回值-WAIT_ABANDONED_0 是放弃的互斥体对象满足等待的对象的数组中的索引。

- WAIT_TIMEOUT

   中指定的超时间隔*dwTimeOut*而无需等待之后过期。

### <a name="remarks"></a>备注

如果*bWaitForAll*为 TRUE，`Lock`将立即同步的所有对象都信号同时成功返回。 如果*bWaitForAll*为 FALSE，`Lock`将一个或多个同步对象发出信号时，就立即返回。

如果`Lock`不能立即返回，它将等待中指定的毫秒数不超过*dwTimeOut*在返回之前的参数。 如果*dwTimeOut*为 INFINITE，`Lock`之前获得对象的访问权限或在指定的条件不会返回*dwWakeMask*已满足。 否则为如果`Lock`已无法获得的同步对象，它将返回成功; 如果不是，它将返回失败。

##  <a name="unlock"></a>  CMultiLock::Unlock

释放所拥有的同步对象`CMultiLock`。

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>参数

*lCount*<br/>
数的引用计数来释放。 必须大于 0。 如果指定的量将导致超过其最大值的对象计数，计数不会更改，并且该函数将返回 FALSE。

*lPrevCount*<br/>
指向一个变量来接收的同步对象的前一个计数。 如果为 NULL，则不返回前一个计数。

### <a name="return-value"></a>返回值

如果函数成功，则非零值否则为 0。

### <a name="remarks"></a>备注

调用此函数`CMultiLock`的析构函数。

第一个窗体`Unlock`尝试解锁由管理的同步对象`CMultiLock`。 第二个窗体`Unlock`尝试解锁`CSemaphore`拥有的对象`CMultiLock`。 如果`CMultiLock`不拥有任何锁定`CSemaphore`对象，则函数返回 FALSE; 否则，返回 TRUE。 *lCount*并*lpPrevCount*是完全相同的参数作为[CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)。 第二种形式的`Unlock`很少适用于 multilock 的情况下。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)
