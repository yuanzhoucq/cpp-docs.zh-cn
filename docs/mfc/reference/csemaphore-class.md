---
title: "CSemaphore 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSemaphore
- AFXMT/CSemaphore
- AFXMT/CSemaphore::CSemaphore
dev_langs: C++
helpviewer_keywords: CSemaphore [MFC], CSemaphore
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0184d013b0a36aeb77bebbba9f6e4ecef47b7f85
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="csemaphore-class"></a>CSemaphore 类
类的对象`CSemaphore`表示一个"信号量"-在一个或多个进程访问资源，并保持当前访问指定的资源的线程数的计数允许有限的数量的线程的同步对象。  
  
## <a name="syntax"></a>语法  
  
```  
class CSemaphore : public CSyncObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CSemaphore::CSemaphore](#csemaphore)|构造 `CSemaphore` 对象。|  
  
## <a name="remarks"></a>备注  
 信号量可用于控制对仅支持有限的数量用户的共享资源的访问。 当前计数`CSemaphore`对象是允许的其他用户数目。 在计数变为零时，所有尝试使用由控制资源**CSemaphore**对象将插入到系统队列并等待，直到它们任一超时或计数高于 0。 构造期间指定的最大可以一次访问受控的资源的用户数`CSemaphore`对象。  
  
 若要使用**CSemaphore**对象，构造`CSemaphore`对象时需要它。 指定你想要等待，信号量的名称和你的应用程序最初应拥有它。 然后，在构造函数将返回时，就可以访问信号量。 调用[CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock)完成后访问受控的资源。  
  
 一种方法来使用`CSemaphore`对象是添加类型的变量的`CSemaphore`为想要控制的类数据成员。 在受控的对象的构造，过程调用的构造函数`CSemaphore`数据成员指定初始访问计数，最大访问次数，信号量 （如果跨进程边界，将使用它） 的名称和所需的安全属性。  
  
 由控制访问资源`CSemaphore`对象以这种方式，先创建任一类型的变量的[CSingleLock](../../mfc/reference/csinglelock-class.md)或类型[CMultiLock](../../mfc/reference/cmultilock-class.md)中资源的访问成员函数。 然后，调用的锁对象`Lock`成员函数 (例如， [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock))。 此时，你的线程将获取对资源的访问，等待要释放并获取访问权限，或者等待的资源要释放和超时值，不能对资源的访问的资源。 在任何情况下，所需的资源已被访问以线程安全的方式。 若要释放资源，使用的锁对象`Unlock`成员函数 (例如， [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock))，或允许未能超出范围的锁对象。  
  
 或者，你可以创建**CSemaphore**对象独立，并尝试访问受控的资源之前对它进行显式访问。 此方法，时更清晰的某个人可以读取你的源代码，是更不易出错。  
  
 有关详细信息如何使用**CSemaphore**对象，请参阅文章[多线程处理： 如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CSemaphore`  
  
## <a name="requirements"></a>要求  
 **标头：** afxmt.h  
  
##  <a name="csemaphore"></a>CSemaphore::CSemaphore  
 命名的或未命名的构造`CSemaphore`对象。  
  
```  
CSemaphore(
    LONG lInitialCount = 1,  
    LONG lMaxCount = 1,  
    LPCTSTR pstrName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```  
  
### <a name="parameters"></a>参数  
 *lInitialCount*  
 初始的使用情况计数的信号。 必须大于或等于 0，并且小于或等于`lMaxCount`。  
  
 `lMaxCount`  
 信号量最大使用率计数。 必须大于 0。  
  
 `pstrName`  
 信号量的名称。 将跨进程边界访问信号量时，必须提供。 如果`NULL`，该对象将为未命名。 如果名称匹配的现有信号，构造函数将生成新`CSemaphore`即在引用该名称的信号量的对象。 如果名称与匹配不是的信号量的现有同步对象，构造将失败。  
  
 *lpsaAttributes*  
 信号量对象的安全属性。 此结构的完整说明，请参阅[SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) Windows SDK 中。  
  
### <a name="remarks"></a>备注  
 若要访问或释放`CSemaphore`对象，请创建[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)对象并调用其[锁](../../mfc/reference/csinglelock-class.md#lock)和[解锁](../../mfc/reference/csinglelock-class.md#unlock)成员函数。  
  
> [!IMPORTANT]
>  在创建后`CSemaphore`对象，请使用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)以确保，互斥体已不存在。 如果互斥体未意外存在，则可能表示一个恶意进程是占用和可能想要恶意使用互斥体。 在这种情况下，建议的安全意识过程是关闭句柄并继续就像在创建对象时失败。  
  
## <a name="see-also"></a>另请参阅  
 [CSyncObject 类](../../mfc/reference/csyncobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)



