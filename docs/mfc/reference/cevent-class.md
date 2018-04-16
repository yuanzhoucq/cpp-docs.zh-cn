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
- CEvent [MFC], CEvent
- CEvent [MFC], PulseEvent
- CEvent [MFC], ResetEvent
- CEvent [MFC], SetEvent
- CEvent [MFC], Unlock
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0646e703f172777817aa569fa28d3430624ccae8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cevent-class"></a>CEvent 类
表示一个事件，即支持一个线程向已发生事件的另一个线程的同步对象。  
  
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
|[CEvent::PulseEvent](#pulseevent)|集到可用事件 （发出信号），释放正在等待的线程，并将事件设置为不可用 （非终止）。|  
|[CEvent::ResetEvent](#resetevent)|设置设为不可用的事件 （非终止）。|  
|[CEvent::SetEvent](#setevent)|将事件设置为可用 （终止） 并释放任何正在等待的线程。|  
|[CEvent::Unlock](#unlock)|释放事件对象。|  
  
## <a name="remarks"></a>备注  
 当一个线程必须知道何时执行其任务时，事件非常有用。 例如，新数据可用时，必须通知将数据复制到的数据存档的线程。 通过使用`CEvent`对象以新数据可用时通知复制线程的线程可以尽快执行其任务。  
  
 `CEvent`对象具有两种类型： 手动和自动。  
  
 自动`CEvent`对象自动返回给是非终止的 （不可用） 状态后释放至少一个线程。 默认情况下，`CEvent`对象是自动的除非您传递`TRUE`为`bManualReset`在构造期间的参数。  
  
 手动`CEvent`对象保留在通过设置状态[SetEvent](#setevent)或[ResetEvent](#resetevent)直到调用其他函数。 若要创建手动`CEvent`对象，则传递`TRUE`为`bManualReset`在构造期间的参数。  
  
 若要使用`CEvent`对象，构造`CEvent`对象需要时。 指定你想要等待，并指定你的应用程序最初应拥有其事件的名称。 然后，就可以访问事件时构造函数将返回。 调用[SetEvent](#setevent)信号 （使之可用） 事件对象，然后调用[解锁](#unlock)完成后访问受控的资源。  
  
 一种方法来使用`CEvent`对象是添加类型的变量的`CEvent`为你想要控制的类数据成员。 在受控的对象的构造，过程调用的构造函数`CEvent`数据成员并指定是否事件最初收到信号，以及 specifythe 类型事件所需的对象，事件 （如果它将使用跨进程的名称边界），和任何所需的安全属性。  
  
 若要访问控制的资源`CEvent`对象以这种方式，请首先创建任一类型的变量的[CSingleLock](../../mfc/reference/csinglelock-class.md)或类型[CMultiLock](../../mfc/reference/cmultilock-class.md)所需的资源的访问方法中。 然后调用`Lock`的锁对象的方法 (例如， [CMultiLock::Lock](../../mfc/reference/cmultilock-class.md#lock))。 此时，你的线程将访问资源、 要释放并获取访问权限，或者等待要释放的资源的资源等待、 下班时间，并无法获得对资源的访问。 在任何情况下，所需的资源已被访问以线程安全的方式。 若要释放资源，调用`SetEvent`信号通知事件对象，然后使用`Unlock`的锁对象的方法 (例如， [CMultiLock::Unlock](../../mfc/reference/cmultilock-class.md#unlock))，或者让不作用域的锁对象。  
  
 有关如何使用`CEvent`对象，请参阅[多线程处理： 如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]  
  
 [!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CEvent`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxmt.h  
  
##  <a name="cevent"></a>CEvent::CEvent  
 命名的或未命名的构造`CEvent`对象。  
  
```  
CEvent(
    BOOL bInitiallyOwn = FALSE,  
    BOOL bManualReset = FALSE,  
    LPCTSTR lpszName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```  
  
### <a name="parameters"></a>参数  
 `bInitiallyOwn`  
 如果**TRUE**的线程**CMultilock**或`CSingleLock`启用对象。 否则，必须等待，想要访问该资源的所有线程。  
  
 *bManualReset*  
 如果**TRUE**，指定事件对象是一个手动的事件，否则事件对象是自动的事件。  
  
 `lpszName`  
 `CEvent` 对象的名称。 如果跨进程边界，将使用该对象必须提供。 如果名称匹配的现有事件，构造函数将生成新`CEvent`即在引用该名称的事件的对象。 如果名称与匹配不是事件的现有同步对象，构造将失败。 如果**NULL**，名称将为 null。  
  
 `lpsaAttribute`  
 事件对象的安全属性。 此结构的完整说明，请参阅[SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) Windows SDK 中。  
  
### <a name="remarks"></a>备注  
 若要访问或释放`CEvent`对象，请创建[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)对象并调用其[锁](../../mfc/reference/csinglelock-class.md#lock)和[解锁](../../mfc/reference/csinglelock-class.md#unlock)成员函数。  
  
 若要更改的状态`CEvent`对象为有信号 （线程无需等待），调用[SetEvent](#setevent)或[PulseEvent](#pulseevent)。 若要设置的状态的`CEvent`为非终止的对象 （线程必须等待），调用[ResetEvent](#resetevent)。  
  
> [!IMPORTANT]
>  在创建后`CEvent`对象，请使用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)以确保互斥体尚不存在。 如果互斥体未意外存在，则可能表示一个恶意进程是占用和可能想要恶意使用互斥体。 在这种情况下，建议的安全意识过程是关闭句柄并继续就像在创建对象时失败。  
  
##  <a name="pulseevent"></a>CEvent::PulseEvent  
 设置要发出信号的事件的状态 （可用）、 释放任何正在等待的线程，并将其重置为非终止 （不可用） 自动。  
  
```  
BOOL PulseEvent();
```  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则为 0。  
  
### <a name="remarks"></a>备注  
 如果事件是手动，所有正在等待的线程的发行，已设置为非终止，事件和`PulseEvent`返回。 如果事件是自动的则释放单个线程，将事件设置为非终止，和`PulseEvent`返回。  
  
 如果没有线程在等待，或可以立即释放无线程`PulseEvent`设置到事件的状态非终止并返回。  
  
 `PulseEvent`使用基础 Win32`PulseEvent`函数，可暂时从等待状态由内核模式异步过程调用。 因此，`PulseEvent`是不可靠，不应由新的应用程序。 有关详细信息，请参阅[PulseEvent 函数](http://msdn.microsoft.com/library/windows/desktop/ms684914)。  
  
##  <a name="resetevent"></a>CEvent::ResetEvent  
 设置到事件的状态非终止之前显式设置为终止通过[SetEvent](#setevent)成员函数。  
  
```  
BOOL ResetEvent();
```  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则为 0。  
  
### <a name="remarks"></a>备注  
 这将导致所有希望访问此事件来等待的线程。  
  
 自动事件不使用此成员函数。  
  
##  <a name="setevent"></a>CEvent::SetEvent  
 释放任何正在等待的线程设置为终止状态，事件的状态。  
  
```  
BOOL SetEvent();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果该函数成功，否则为 0。  
  
### <a name="remarks"></a>备注  
 如果事件是手动，则事件将保持终止状态，直到[ResetEvent](#resetevent)调用。 可以在这种情况下释放多个线程。 如果事件是自动的该事件将保留发送信号，直至释放一个线程。 然后，系统会将事件状态设置为非终止。 如果没有线程在等待，一直保持状态，终止状态之前则释放一个线程。  
  
##  <a name="unlock"></a>CEvent::Unlock  
 释放事件对象。  
  
```  
BOOL Unlock();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果线程拥有事件对象和事件都是自动事件;否则为 0。  
  
### <a name="remarks"></a>备注  
 由当前拥有自动事件来释放它后它们完成后，如果要重复使用其锁定对象的线程调用此成员函数。 如果的锁对象不是可重复使用，则将锁定对象的析构函数通过调用此函数。  
  
## <a name="see-also"></a>请参阅  
 [CSyncObject 类](../../mfc/reference/csyncobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)

