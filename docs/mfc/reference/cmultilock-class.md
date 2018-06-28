---
title: CMultiLock 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMultiLock
- AFXMT/CMultiLock
- AFXMT/CMultiLock::CMultiLock
- AFXMT/CMultiLock::IsLocked
- AFXMT/CMultiLock::Lock
- AFXMT/CMultiLock::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CMultiLock [MFC], CMultiLock
- CMultiLock [MFC], IsLocked
- CMultiLock [MFC], Lock
- CMultiLock [MFC], Unlock
ms.assetid: c5b7c78b-1f81-4387-b7dd-2c813c5b6b61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3e578d3aece15f191bfad858923470d09bede74
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37039795"
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
|[CMultiLock::IsLocked](#islocked)|确定是否锁定一个特定的同步对象数组中。|  
|[CMultiLock::Lock](#lock)|等待同步对象的数组。|  
|[CMultiLock::Unlock](#unlock)|释放任何拥有的同步对象。|  
  
## <a name="remarks"></a>备注  
 `CMultiLock` 没有基类。  
  
 若要使用同步类[CSemaphore](../../mfc/reference/csemaphore-class.md)， [CMutex](../../mfc/reference/cmutex-class.md)，和[CEvent](../../mfc/reference/cevent-class.md)，你可以创建`CMultiLock`或[CSingleLock](../../mfc/reference/csinglelock-class.md)等待并释放同步对象的对象。 使用`CMultiLock`时有多个对象，你无法使用在特定的时间。 使用`CSingleLock`时只需一次等待上一个对象。  
  
 若要使用`CMultiLock`对象，请首先创建想要等待同步对象的数组。 接下来，调用`CMultiLock`受控的资源的类中的成员函数内的对象的构造函数。 然后调用[锁](#lock)成员函数以确定是否有可用资源 （发出信号）。 如果一个对象，则继续而成员函数的其余部分。 如果没有任何资源可用，等待经过指定的资源要释放的时间量，或返回失败。 使用的资源已完成后，请调用[解锁](#unlock)函数如果`CMultiLock`对象是同样，使用或允许`CMultiLock`对象将其销毁。  
  
 `CMultiLock` 对象是最有用的当线程必须大量的`CEvent`对象能够响应。 创建包含所有数组`CEvent`指针，并调用`Lock`。 这将导致要等待，直到事件之一处于有信号状态的线程。  
  
 有关详细信息如何使用`CMultiLock`对象，请参阅文章[多线程处理： 如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
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
 *ppObjects*  
 指向要等待的同步对象的指针的数组。 不能为**NULL**。  
  
 *dwCount*  
 中的对象数*ppObjects*。 必须大于 0。  
  
 *bInitialLock*  
 指定是否以最初尝试访问的任何提供的对象。  
  
### <a name="remarks"></a>备注  
 在创建的同步对象等待数组后调用此函数。 它通常从调用线程必须等待可用的同步对象之一中。  
  
##  <a name="islocked"></a>  CMultiLock::IsLocked  
 确定指定的对象是否为非终止 （不可用）。  
  
```  
BOOL IsLocked(DWORD dwItem);
```  
  
### <a name="parameters"></a>参数  
 *dwItem*  
 对应于正在查询其状态的对象的对象的数组中的索引。  
  
### <a name="return-value"></a>返回值  
 如果指定的对象被锁定; 则为非 0否则为 0。  
  
##  <a name="lock"></a>  CMultiLock::Lock  
 调用此函数可访问一个或多个由提供给的同步对象控制的资源`CMultiLock`构造函数。  
  
```  
DWORD Lock(
    DWORD dwTimeOut = INFINITE,  
    BOOL bWaitForAll = TRUE,  
    DWORD dwWakeMask = 0);
```  
  
### <a name="parameters"></a>参数  
 *dwTimeOut*  
 指定要等待同步对象可用的时间量 （发出信号）。 如果**无限**，`Lock`将等待，直到该对象在返回之前处于有信号状态。  
  
 *bWaitForAll*  
 指定是否必须都变为等待状态的所有对象终止都状态在同一时间在返回之前。 如果**FALSE**，`Lock`时等待的对象之一处于有信号状态将返回。  
  
 *dwWakeMask*  
 指定允许中止等待其他条件。 此参数的可用选项的完整列表，请参阅[MsgWaitForMultipleObjects](http://msdn.microsoft.com/library/windows/desktop/ms684242) Windows SDK 中。  
  
### <a name="return-value"></a>返回值  
 如果`Lock`失败，它将返回-1。 如果成功，它将返回下列值之一：  
  
-   之间**WAIT_OBJECT_0**和**WAIT_OBJECT_0** + （对象-1 的数）  
  
     如果*bWaitForAll*是**TRUE**，所有对象都已都终止 （可用）。 如果*bWaitForAll*是**FALSE**，返回值- **WAIT_OBJECT_0**是处于有信号状态的对象的对象的数组中的索引 （可用）。  
  
- **WAIT_OBJECT_0** + （的对象数）  
  
     事件中指定*dwWakeMask*可用线程的输入队列中。  
  
-   之间**WAIT_ABANDONED_0**和**WAIT_ABANDONED_0** + （对象-1 的数）  
  
     如果*bWaitForAll*是**TRUE**，所有对象都已都终止，而至少一个对象是一个放弃的 mutex 对象。 如果*bWaitForAll*是**FALSE**，返回值- **WAIT_ABANDONED_0**是放弃的 mutex 对象满足等待的对象的数组中的索引。  
  
- **WAIT_TIMEOUT**  
  
     中指定的超时间隔*dwTimeOut*而无需等待之后过期。  
  
### <a name="remarks"></a>备注  
 如果*bWaitForAll*是**TRUE**，`Lock`将成功后立即返回同步的所有对象都变为同时终止都状态。 如果*bWaitForAll*是**FALSE**，`Lock`将一个或多个同步对象将被发送信号时，就会立即返回。  
  
 如果`Lock`不能立即返回，它将等待中指定的毫秒数不超过*dwTimeOut*在返回之前的参数。 如果*dwTimeOut*是**无限**，`Lock`直到获得访问的对象时或在指定了一个条件，将不会返回*dwWakeMask*得到满足而。 否则为如果`Lock`已无法获得的同步对象，它将返回成功; 如果不是，它将返回失败。  
  
##  <a name="unlock"></a>  CMultiLock::Unlock  
 释放所拥有的同步对象`CMultiLock`。  
  
```  
BOOL Unlock();

 
BOOL Unlock(
    LONG lCount,  
    LPLONG lPrevCount = NULL);
```  
  
### <a name="parameters"></a>参数  
 *lCount*  
 参考编号计数以释放。 必须大于 0。 如果指定的量将导致超过其最大值的对象的计数，计数未发生更改，并且该函数将返回**FALSE**。  
  
 *lPrevCount*  
 指向要接收同步对象的前一个计数的变量。 如果**NULL**，则不返回前一个计数。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此函数`CMultiLock`的析构函数。  
  
 第一种形式的`Unlock`尝试解锁管理的同步对象`CMultiLock`。 第二种形式的`Unlock`尝试解锁`CSemaphore`拥有的对象`CMultiLock`。 如果`CMultiLock`不拥有任何锁定`CSemaphore`对象，该函数将返回**FALSE**; 否则为它将返回**TRUE**。 *lCount*和*lpPrevCount*时完全相同的参数作为[CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)。 第二种形式的`Unlock`很少适用于 multilock 的情况下。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)



