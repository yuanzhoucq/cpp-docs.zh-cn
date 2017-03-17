---
title: "CSemaphore 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSemaphore
- AFXMT/CSemaphore
- AFXMT/CSemaphore::CSemaphore
dev_langs:
- C++
helpviewer_keywords:
- synchronization objects, semaphores
- CSemaphore class
- semaphores
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
caps.latest.revision: 23
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
ms.openlocfilehash: 31de1e553ea2facea6b70c284aecdbf10e22c89f
ms.lasthandoff: 02/24/2017

---
# <a name="csemaphore-class"></a>CSemaphore 类
类的对象`CSemaphore`表示一个"信号量"-允许访问资源，并保持一个或多个进程中当前访问指定的资源的线程数的有限的数量的线程的同步对象。  
  
## <a name="syntax"></a>语法  
  
```  
class CSemaphore : public CSyncObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CSemaphore::CSemaphore](#csemaphore)|构造 `CSemaphore` 对象。|  
  
## <a name="remarks"></a>备注  
 信号量是用于控制对仅支持有限的数量用户的共享资源的访问。 当前计数`CSemaphore`对象是允许的其他用户的数目。 所有计数达到零时，当尝试使用由控制资源**CSemaphore**对象将插入到系统队列并等待，直到它们任一超时或计数大于 0。 构造期间指定的最大可以一次访问受控的资源的用户数`CSemaphore`对象。  
  
 若要使用**CSemaphore**对象，请构造`CSemaphore`对象时需要它。 指定您希望我们等一下，信号量的名称和您的应用程序最初应拥有该域。 在构造函数将返回时，您就可以访问信号量。 调用[CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock)完成后访问受控的资源。  
  
 一种方法来使用`CSemaphore`对象是添加类型的变量`CSemaphore`为您希望控件的类数据成员。 受控制的对象的构造，期间调用的构造函数`CSemaphore`指定初始数据成员访问计数、 最大访问次数、 信号量 （如果它将用于跨进程边界），名称和所需的安全属性。  
  
 通过控制访问资源`CSemaphore`对象以这种方式，先创建任一类型的变量[CSingleLock](../../mfc/reference/csinglelock-class.md)或类型[CMultiLock](../../mfc/reference/cmultilock-class.md)中资源的访问成员函数。 然后，调用的锁对象`Lock`成员函数 (例如， [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock))。 此时，您的线程将获得对资源的访问，等待被释放和获得访问权限，或等待要释放的资源和超时，无法访问该资源的资源。 在任何情况下，所需的资源已访问以线程安全的方式。 若要释放资源，使用的锁对象`Unlock`成员函数 (例如， [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock))，或允许离开作用域的锁对象。  
  
 或者，可以创建**CSemaphore**对象独立的并且在尝试访问受控的资源之前显式访问它。 这种方法，同时更清晰的给人读取您的源代码是比较容易出错。  
  
 有关如何使用**CSemaphore**对象，请参阅文章[多线程处理︰ 如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CSemaphore`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxmt.h  
  
##  <a name="csemaphore"></a>CSemaphore::CSemaphore  
 构造的已命名的或未命名`CSemaphore`对象。  
  
```  
CSemaphore(
    LONG lInitialCount = 1,  
    LONG lMaxCount = 1,  
    LPCTSTR pstrName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```  
  
### <a name="parameters"></a>参数  
 *lInitialCount*  
 信号量的初始使用情况计数。 必须是大于或等于 0，且小于或等于`lMaxCount`。  
  
 `lMaxCount`  
 信号量的最大使用量计数。 必须大于 0。  
  
 `pstrName`  
 信号量的名称。 将跨进程边界访问信号量时，必须提供。 如果`NULL,`将未命名对象。 如果名称匹配现有的信号量，该构造函数将生成新`CSemaphore`引用该名称的信号量的对象。 如果名称匹配不是一个信号量的现有同步对象，构造将会失败。  
  
 *lpsaAttributes*  
 信号量对象的安全属性。 此结构的完整说明，请参阅[SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 若要访问或释放`CSemaphore`对象，请创建[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)对象，并调用其[锁](../../mfc/reference/csinglelock-class.md#lock)和[解锁](../../mfc/reference/csinglelock-class.md#unlock)成员函数。  
  
> [!IMPORTANT]
>  在创建后`CSemaphore`对象，请使用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)以确保，互斥体已不存在。 如果互斥体未存在意外，这可能表示一个恶意进程占用并可能想要出于恶意使用互斥体。 在这种情况下，建议的注重安全的过程是关闭句柄并继续像创建对象时出错。  
  
## <a name="see-also"></a>另请参阅  
 [CSyncObject 类](../../mfc/reference/csyncobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)




