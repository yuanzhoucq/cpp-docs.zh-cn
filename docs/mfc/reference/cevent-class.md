---
title: "CEvent 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- synchronization objects, event
- synchronization classes, CEvent class
- CEvent class
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
caps.latest.revision: 27
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 9edadeec87cf04ae6166c173c65463d1509eb1d8
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cevent-class"></a>CEvent 类
表示一个事件，即支持一个线程通知事件已发生的另一个线程的同步对象。  
  
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
|[CEvent::PulseEvent](#pulseevent)|设置为用事件 （信号），释放正在等待的线程，并将事件设置为不可用 （非终止）。|  
|[CEvent::ResetEvent](#resetevent)|将事件设置为不可用 （非终止）。|  
|[CEvent::SetEvent](#setevent)|将事件设置为可用 （终止） 并释放任何正在等待的线程。|  
|[CEvent::Unlock](#unlock)|释放事件对象。|  
  
## <a name="remarks"></a>备注  
 当一个线程必须知道何时执行其任务时，事件非常有用。 例如，在新数据可用时，必须通知线程将数据复制到数据存档。 通过使用`CEvent`对象时要通知的副本线程新数据是否可用，线程可以尽可能快地执行其任务。  
  
 `CEvent`对象具有两种类型︰ 手动和自动。  
  
 自动`CEvent`对象会自动返回为非终止 （不可用） 状态后至少一个线程被释放。 默认情况下，`CEvent`对象是自动的除非您传递`TRUE`为`bManualReset`在构造期间的参数。  
  
 手动`CEvent`对象而保留在设置的状态[SetEvent](#setevent)或[ResetEvent](#resetevent)直到调用其他函数。 若要创建手动`CEvent`对象，将传递`TRUE`为`bManualReset`在构造期间的参数。  
  
 若要使用`CEvent`对象，请构造`CEvent`时需要它的对象。 指定要等待，并指定您的应用程序最初应拥有它的事件的名称。 然后，您可以访问时构造函数将返回的事件。 调用[SetEvent](#setevent)信号 （使之可用） 事件对象，然后调用[解锁](#unlock)完成后访问受控的资源。  
  
 一种方法来使用`CEvent`对象是添加类型的变量`CEvent`为你想要控制的类数据成员。 受控制的对象的构造，期间调用的构造函数`CEvent`数据成员并指定是否事件最初收到信号，以及 specifythe 对象类型的事件所需的事件 （如果它将用于跨进程边界），名称和任何安全性属性您想。  
  
 若要访问控制的资源`CEvent`对象以这种方式，请首先创建任一类型的变量[CSingleLock](../../mfc/reference/csinglelock-class.md)或类型[CMultiLock](../../mfc/reference/cmultilock-class.md)所需的资源的访问方法中。 然后，调用`Lock`的锁对象的方法 (例如， [CMultiLock::Lock](../../mfc/reference/cmultilock-class.md#lock))。 此时，您的线程将访问资源、 等待释放和获得访问权限，或等待要释放的资源的资源、 超时值，并无法获得对资源的访问。 在任何情况下，所需的资源已访问以线程安全的方式。 若要释放资源，调用`SetEvent`信号通知事件对象，然后使用`Unlock`的锁对象的方法 (例如， [CMultiLock::Unlock](../../mfc/reference/cmultilock-class.md#unlock))，或让离开作用域的锁对象。  
  
 有关如何使用`CEvent`对象，请参阅[多线程处理︰ 如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities #&45;](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]  
  
 [!code-cpp[NVC_MFC_Utilities #&46;](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CEvent`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxmt.h  
  
##  <a name="cevent"></a>CEvent::CEvent  
 构造的已命名的或未命名`CEvent`对象。  
  
```  
CEvent(
    BOOL bInitiallyOwn = FALSE,  
    BOOL bManualReset = FALSE,  
    LPCTSTR lpszName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```  
  
### <a name="parameters"></a>参数  
 `bInitiallyOwn`  
 如果**TRUE**的线程**CMultilock**或`CSingleLock`对象已启用。 否则，必须等待，想要访问该资源的所有线程。  
  
 *bManualReset*  
 如果**TRUE**，指定的事件对象是一个手动的事件，否则事件对象是自动的事件。  
  
 `lpszName`  
 `CEvent` 对象的名称。 如果该对象将使用跨进程边界，必须提供。 如果名称与现有的事件相匹配，该构造函数将生成新`CEvent`引用该名称的事件的对象。 如果名称与一个现有的同步对象，它不事件相匹配，构造将会失败。 如果**NULL**，名称将为 null。  
  
 `lpsaAttribute`  
 事件对象的安全属性。 此结构的完整说明，请参阅[SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 若要访问或释放`CEvent`对象，请创建[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)对象，并调用其[锁](../../mfc/reference/csinglelock-class.md#lock)和[解锁](../../mfc/reference/csinglelock-class.md#unlock)成员函数。  
  
 若要更改的状态`CEvent`对象发出信号 （线程不必等待），调用[SetEvent](#setevent)或[PulseEvent](#pulseevent)。 若要设置的状态的`CEvent`对象传递给非终止 （线程必须等待），调用[ResetEvent](#resetevent)。  
  
> [!IMPORTANT]
>  在创建后`CEvent`对象，请使用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)以确保该互斥体尚不存在。 如果互斥体未存在意外，这可能表示一个恶意进程占用并可能想要出于恶意使用互斥体。 在这种情况下，建议的注重安全的过程是关闭句柄并继续像创建对象时出错。  
  
##  <a name="pulseevent"></a>CEvent::PulseEvent  
 设置发出信号的事件的状态 （可用）、 释放任何正在等待的线程，并将其重置为非终止 （不可用） 自动。  
  
```  
BOOL PulseEvent();
```  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 如果该事件是手动，所有等待的线程被都释放，则将事件设置为非终止，并`PulseEvent`返回。 如果该事件是自动的单个线程被释放，则将事件设置为非终止，并`PulseEvent`返回。  
  
 如果没有线程在等待，或没有线程可能会立即释放`PulseEvent`将的事件的状态设置为非终止，并返回。  
  
 `PulseEvent`将使用基础 Win32`PulseEvent`函数，可暂时从等待状态由内核模式下异步过程调用。 因此，`PulseEvent`是不现实，而且不能由新的应用程序。 有关详细信息，请参阅[PulseEvent 函数](http://msdn.microsoft.com/library/windows/desktop/ms684914)。  
  
##  <a name="resetevent"></a>CEvent::ResetEvent  
 设置为事件的状态非终止之前显式设置为终止的[SetEvent](#setevent)成员函数。  
  
```  
BOOL ResetEvent();
```  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 这将导致所有想要访问此事件，以等待的线程。  
  
 自动事件不使用此成员函数。  
  
##  <a name="setevent"></a>CEvent::SetEvent  
 释放任何正在等待的线程的情况下设置为终止状态，该事件的状态。  
  
```  
BOOL SetEvent();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果该函数成功，否则为 0。  
  
### <a name="remarks"></a>备注  
 如果该事件是手动，事件仍将终止状态，直到[ResetEvent](#resetevent)调用。 多个线程可能会在这种情况下释放。 如果该事件是自动的该事件会保持已发出信号，直至单个线程被释放。 然后，系统会将事件状态设置为非终止。 如果没有线程在等待，状态将保持已发出信号，直到释放一个线程。  
  
##  <a name="unlock"></a>CEvent::Unlock  
 释放事件对象。  
  
```  
BOOL Unlock();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果线程所拥有的事件对象和事件都是自动事件;否则为 0。  
  
### <a name="remarks"></a>备注  
 由当前拥有一个自动事件，它将其释放后它们完成后，如果要重复使用其锁对象的线程调用此成员函数。 如果锁对象不是可重复使用，锁对象的析构函数将调用此函数。  
  
## <a name="see-also"></a>另请参阅  
 [CSyncObject 类](../../mfc/reference/csyncobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)


