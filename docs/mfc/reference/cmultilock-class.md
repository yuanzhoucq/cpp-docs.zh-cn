---
title: "CMultiLock 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMultiLock
dev_langs:
- C++
helpviewer_keywords:
- CMultiLock class
- synchronization objects, access control
ms.assetid: c5b7c78b-1f81-4387-b7dd-2c813c5b6b61
caps.latest.revision: 20
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: a58d59d8e4d7a1c542dee80295dd8eef6c8be338
ms.lasthandoff: 02/24/2017

---
# <a name="cmultilock-class"></a>CMultiLock 类
表示多线程程序中用于控制对多个资源的访问的访问控制机制。  
  
## <a name="syntax"></a>语法  
  
```  
class CMultiLock  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMultiLock::CMultiLock](#cmultilock)|构造 `CMultiLock` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMultiLock::IsLocked](#islocked)|确定是否在数组中的特定的同步对象将被锁定。|  
|[CMultiLock::Lock](#lock)|等待同步对象的数组。|  
|[CMultiLock::Unlock](#unlock)|释放任何拥有的同步对象。|  
  
## <a name="remarks"></a>备注  
 `CMultiLock`没有基类的类。  
  
 若要使用同步类[CSemaphore](../../mfc/reference/csemaphore-class.md)， [CMutex](../../mfc/reference/cmutex-class.md)，和[CEvent](../../mfc/reference/cevent-class.md)，您可以创建**CMultiLock**或[CSingleLock](../../mfc/reference/csinglelock-class.md)对象等待，并释放同步对象。 使用**CMultiLock**时有多个可以使用某一时刻的对象。 使用`CSingleLock`时只需一次针对一个对象的等待。  
  
 若要使用**CMultiLock**对象，请首先创建您想要等待同步对象的数组。 接下来，调用**CMultiLock**受控的资源的类中的成员函数内的对象的构造函数。 然后，调用[锁](#lock)成员函数来确定某个资源是否可用 （终止）。 如果一个对象，继续使用该成员函数的其余部分。 如果没有任何资源可用，等待指定数量的资源要释放的时间，或返回失败。 使用的资源已完成后，或者调用[解锁](#unlock)函数如果**CMultiLock**对象是同样，使用或允许**CMultiLock**对象将其销毁。  
  
 **CMultiLock**线程不具有数很大时，对象才最有用`CEvent`可以响应的对象。 创建一个数组，包含所有`CEvent`指针，并调用`Lock`。 这将导致线程一直等待，直到其中一个事件终止状态。  
  
 有关如何使用**CMultiLock**对象，请参阅文章[多线程处理︰ 如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CMultiLock`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxmt.h  
  
##  <a name="a-namecmultilocka--cmultilockcmultilock"></a><a name="cmultilock"></a>CMultiLock::CMultiLock  
 构造**CMultiLock**对象。  
  
```  
CMultiLock(
    CSyncObject* ppObjects [ ],  
    DWORD dwCount,  
    BOOL bInitialLock = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `ppObjects`  
 等待同步对象的指针的数组。 不能为**NULL**。  
  
 `dwCount`  
 中的对象数`ppObjects`。 必须大于 0。  
  
 `bInitialLock`  
 指定是否以最初尝试访问的任何提供的对象。  
  
### <a name="remarks"></a>备注  
 在创建的同步对象等待数组后调用此函数。 它通常从内部调用的线程必须等待一个同步对象变得可用。  
  
##  <a name="a-nameislockeda--cmultilockislocked"></a><a name="islocked"></a>CMultiLock::IsLocked  
 确定指定的对象是否为非终止 （不可用）。  
  
```  
BOOL IsLocked(DWORD dwItem);
```  
  
### <a name="parameters"></a>参数  
 *dwItem*  
 要查询其状态的对象所对应的对象的数组中的索引。  
  
### <a name="return-value"></a>返回值  
 如果指定的对象被锁定，则非零值否则为 0。  
  
##  <a name="a-namelocka--cmultilocklock"></a><a name="lock"></a>CMultiLock::Lock  
 调用此函数可获取对一个或多个由提供给同步对象控制的资源访问权限**CMultiLock**构造函数。  
  
```  
DWORD Lock(
    DWORD dwTimeOut = INFINITE,  
    BOOL bWaitForAll = TRUE,  
    DWORD dwWakeMask = 0);
```  
  
### <a name="parameters"></a>参数  
 *dwTimeOut*  
 指定要等待同步对象可用的时间量 （终止）。 如果**无限**，`Lock`将等待，直到在返回之前，该对象处于终止状态。  
  
 `bWaitForAll`  
 指定等待的所有对象是否必须在返回前同时接收都信号。 如果**FALSE**，`Lock`将返回在任何一个等待的对象发出信号。  
  
 `dwWakeMask`  
 指定有权中止等待其他条件。 此参数的可用选项的完整列表，请参阅[MsgWaitForMultipleObjects](http://msdn.microsoft.com/library/windows/desktop/ms684242)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 如果`Lock`失败，它将返回 – 1。 如果成功，它将返回下列值之一︰  
  
-   之间**WAIT_OBJECT_0**和**WAIT_OBJECT_0** + （的对象 – 1 的数）  
  
     如果`bWaitForAll`是**TRUE**，所有对象都已都终止 （可用）。 如果`bWaitForAll`是**FALSE**，则返回值 – **WAIT_OBJECT_0**是中的对象处于终止状态的对象的数组的索引 （可用）。  
  
- **WAIT_OBJECT_0** + （的对象数）  
  
     事件中指定`dwWakeMask`线程的输入队列中可用。  
  
-   之间**WAIT_ABANDONED_0**和**WAIT_ABANDONED_0** + （的对象 – 1 的数）  
  
     如果`bWaitForAll`是**TRUE**，所有对象都已都终止，而至少一个对象是一个放弃的 mutex 对象。 如果`bWaitForAll`是**FALSE**，则返回值 – **WAIT_ABANDONED_0**是放弃的 mutex 对象满足等待的对象的数组中的索引。  
  
- **WAIT_TIMEOUT**  
  
     中指定的超时间隔*dwTimeOut*不等待成功过期。  
  
### <a name="remarks"></a>备注  
 如果`bWaitForAll`是**TRUE**，`Lock`将成功后立即返回同步的所有对象都变为同时终止都状态。 如果`bWaitForAll`是**FALSE**，`Lock`将立即返回一个或多个同步对象将被发送信号。  
  
 如果`Lock`不能立即返回，它将等待中指定的毫秒数不超过*dwTimeOut*在返回之前的参数。 如果*dwTimeOut*是**无限**，`Lock`直到获得对象的访问权限或在指定了一个条件，将不会返回`dwWakeMask`已满足。 否则为如果`Lock`是诱使受害者的同步对象，它将返回成功; 如果不是，它将返回失败。  
  
##  <a name="a-nameunlocka--cmultilockunlock"></a><a name="unlock"></a>CMultiLock::Unlock  
 释放同步对象归`CMultiLock`。  
  
```  
BOOL Unlock();

 
BOOL Unlock(
    LONG lCount,  
    LPLONG lPrevCount = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lCount`  
 参考编号计数以释放。 必须大于 0。 如果指定的量会导致对象的计数超出其最大值，计数未发生更改时，该函数将返回**FALSE**。  
  
 `lPrevCount`  
 指向一个变量来接收的同步对象的前一个计数。 如果**NULL**，则不返回前一个计数。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此函数`CMultiLock`的析构函数。  
  
 第一个窗体`Unlock`尝试解锁由管理的同步对象`CMultiLock`。 第二种形式的`Unlock`尝试解锁`CSemaphore`拥有的对象`CMultiLock`。 如果`CMultiLock`不拥有任何锁定`CSemaphore`对象，该函数将返回**FALSE**; 否则为它将返回**TRUE**。 `lCount`和`lpPrevCount`是完全相同的参数作为[CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)。 第二种形式的`Unlock`很少适用于 multilock 的情况下。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)




