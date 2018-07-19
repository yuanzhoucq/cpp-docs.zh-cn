---
title: CEvent 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CEvent
- AFXMT/CEvent
- AFXMT/CEvent::CEvent
- AFXMT/CEvent::PulseEvent
- AFXMT/CEvent::ResetEvent
- AFXMT/CEvent::SetEvent
- AFXMT/CEvent::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CEvent [MFC], CEvent
- CEvent [MFC], PulseEvent
- CEvent [MFC], ResetEvent
- CEvent [MFC], SetEvent
- CEvent [MFC], Unlock
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f31d5d04638685b6d7636f40108b7e95bbd5d37
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338820"
---
# <a name="cevent-class"></a>CEvent 类
表示一个事件，这是支持一个线程通知另一个事件发生的同步对象。  
  
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
|[CEvent::PulseEvent](#pulseevent)|集到可用事件 （信号），释放等待线程，并将事件设置为不可用 （非终止）。|  
|[CEvent::ResetEvent](#resetevent)|将事件设置为不可用 （非终止）。|  
|[CEvent::SetEvent](#setevent)|将事件设置为可用 （已发出信号） 并释放任何正在等待的线程。|  
|[CEvent::Unlock](#unlock)|释放事件对象。|  
  
## <a name="remarks"></a>备注  
 当一个线程必须知道何时执行其任务时，事件非常有用。 例如，当新数据可用时，必须通知线程将数据复制到数据存档。 通过使用`CEvent`对象以新数据可用时通知复制线程的线程可以尽快执行其任务。  
  
 `CEvent` 对象具有两种类型： 手动和自动。  
  
 自动`CEvent`对象自动返回到非信号 （不可用） 状态后至少一个线程被释放。 默认情况下`CEvent`对象是自动的除非传入`TRUE`有关*bManualReset*在构造期间的参数。  
  
 手动`CEvent`对象中设置的状态保持[SetEvent](#setevent)或[ResetEvent](#resetevent)直到调用其他函数。 若要创建手动`CEvent`对象，传递`TRUE`为`bManualReset`在构造期间的参数。  
  
 若要使用`CEvent`对象，构造`CEvent`对象在需要时。 指定所需等待，并请指定你的应用程序最初应拥有它的事件的名称。 然后，您可以访问时构造函数将返回的事件。 调用[SetEvent](#setevent)信号 （使之可用） 事件对象，然后调用[解锁](#unlock)完成后访问受控的资源。  
  
 使用一种替代方法`CEvent`对象将添加一个类型的变量`CEvent`为你想要控制此类数据成员。 在受控的对象的构造，过程调用的构造函数`CEvent`数据成员，并指定是否事件最初处于终止状态，以及 specifythe 类型的事件对象所需的事件 （如果它将使用跨进程名称边界），和任何所需的安全属性。  
  
 若要访问控制的资源`CEvent`对象以这种方式，请首先创建任一类型的变量[CSingleLock](../../mfc/reference/csinglelock-class.md)或类型[CMultiLock](../../mfc/reference/cmultilock-class.md)中所需的资源的访问方法。 然后调用`Lock`锁定对象的方法 (例如， [CMultiLock::Lock](../../mfc/reference/cmultilock-class.md#lock))。 此时，你的线程将访问资源、 等待资源释放和获取访问权限，或等待资源释放、 超时时间，并无法获取对资源的访问权限。 在任何情况下，以线程安全的方式访问所需的资源。 若要释放资源，请调用`SetEvent`信号通知事件对象，然后使用`Unlock`锁对象的方法 (例如， [CMultiLock::Unlock](../../mfc/reference/cmultilock-class.md#unlock))，或让离开作用域的锁对象。  
  
 有关如何使用详细信息`CEvent`对象，请参阅[多线程处理： 如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]  
  
 [!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CEvent`  
  
## <a name="requirements"></a>要求  
 **标头：** afxmt.h  
  
##  <a name="cevent"></a>  CEvent::CEvent  
 构造一个已命名或未命名的`CEvent`对象。  
  
```  
CEvent(
    BOOL bInitiallyOwn = FALSE,  
    BOOL bManualReset = FALSE,  
    LPCTSTR lpszName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```  
  
### <a name="parameters"></a>参数  
 *bInitiallyOwn*  
 如果为 TRUE，对于线程`CMultilock`或`CSingleLock`对象已启用。 否则，必须等待，想要访问的资源的所有线程。  
  
 *bManualReset*  
 如果为 TRUE，则指定事件对象手动事件，否则事件对象是自动的事件。  
  
 *lpszName*  
 `CEvent` 对象的名称。 如果将跨进程边界使用的对象必须提供。 如果名称匹配的现有事件，构造函数将生成新`CEvent`对象引用该名称的事件。 如果名称与现有同步对象的不是事件相匹配，则构造将失败。 如果为 NULL，则名称将为 null。  
  
 *lpsaAttribute*  
 事件对象的安全特性。 此结构的完整说明，请参阅[SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) Windows SDK 中。  
  
### <a name="remarks"></a>备注  
 访问或释放`CEvent`对象，请创建[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)对象，并调用其[锁](../../mfc/reference/csinglelock-class.md#lock)并[解锁](../../mfc/reference/csinglelock-class.md#unlock)成员函数。  
  
 若要更改的状态`CEvent`对象为终止状态 （线程不必等待），调用[SetEvent](#setevent)或[PulseEvent](#pulseevent)。 若要设置的状态`CEvent`为非终止的对象 （线程必须等待），调用[ResetEvent](#resetevent)。  
  
> [!IMPORTANT]
>  在创建后`CEvent`对象，请使用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)以确保该互斥体的位置不存在。 如果该互斥体未意外存在，则可能表示一个恶意进程是占用并可能想要出于恶意使用互斥体。 在这种情况下，建议的注重安全的过程是关闭句柄并继续执行，如同创建对象时出错。  
  
##  <a name="pulseevent"></a>  CEvent::PulseEvent  
 设置要发出信号的事件的状态 （可用）、 释放任何正在等待的线程，并将其重置为非终止 （不可用） 自动。  
  
```  
BOOL PulseEvent();
```  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 如果事件是手动的所有等待线程的都发行，将事件设置为非终止，和`PulseEvent`返回。 如果该事件是自动的单个线程被释放，将事件设置为非终止，和`PulseEvent`返回。  
  
 如果没有线程处于等待状态，或没有线程可以立即释放`PulseEvent`到事件状态设置非终止，并返回。  
  
 `PulseEvent` 使用基础 Win32`PulseEvent`函数，可暂时从等待状态的内核模式下异步过程调用。 因此，`PulseEvent`不可靠，因此不应通过新的应用程序。 有关详细信息，请参阅[PulseEvent 函数](http://msdn.microsoft.com/library/windows/desktop/ms684914)。  
  
##  <a name="resetevent"></a>  CEvent::ResetEvent  
 设置的状态的事件信号之前显式设置为终止通过[SetEvent](#setevent)成员函数。  
  
```  
BOOL ResetEvent();
```  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 这将导致所有想要访问此事件来等待的线程。  
  
 自动事件不使用此成员函数。  
  
##  <a name="setevent"></a>  CEvent::SetEvent  
 设置为终止状态，将事件状态释放任何正在等待的线程。  
  
```  
BOOL SetEvent();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果函数成功，否则为 0。  
  
### <a name="remarks"></a>备注  
 如果该事件是手动的该事件将保持终止状态，直到[ResetEvent](#resetevent)调用。 可以在这种情况下发布多个线程。 如果该事件是自动的事件将保持已发出信号，释放一个线程之前。 然后，系统会将事件状态设置为非终止。 如果没有线程在等待，状态保持终止状态，直到一个线程被释放。  
  
##  <a name="unlock"></a>  CEvent::Unlock  
 释放事件对象。  
  
```  
BOOL Unlock();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果线程拥有事件对象和事件是一种自动事件;否则为 0。  
  
### <a name="remarks"></a>备注  
 由当前拥有的自动事件来释放它后它们完成后，如果要重复使用其锁对象的线程调用此成员函数。 如果不希望重复使用的锁对象，该锁对象的析构函数将调用此函数。  
  
## <a name="see-also"></a>请参阅  
 [CSyncObject 类](../../mfc/reference/csyncobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)

