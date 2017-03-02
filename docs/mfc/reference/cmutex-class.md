---
title: "CMutex 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- Mutex
- CMutex
dev_langs:
- C++
helpviewer_keywords:
- CMutex class
- synchronization classes, CMutex class
- synchronization objects, mutex
- mutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
caps.latest.revision: 22
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
ms.openlocfilehash: 159f2e02dfe44d74ebcaad687a23cef734b61fc9
ms.lasthandoff: 02/24/2017

---
# <a name="cmutex-class"></a>CMutex 类
表示一个"互斥体"— 一个允许一个线程互相排斥的方式访问资源的同步对象。  
  
## <a name="syntax"></a>语法  
  
```  
class CMutex : public CSyncObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMutex::CMutex](#cmutex)|构造 `CMutex` 对象。|  
  
## <a name="remarks"></a>备注  
 当一次只有一个线程有权修改数据或其他受控制的资源，互斥锁非常有用。 例如，将节点添加到链接的列表是一个过程，它应只允许一个线程通过一次。 通过使用`CMutex`对象来控制在链接的列表，仅一次一个线程可以访问该列表。  
  
 若要使用`CMutex`对象，请构造`CMutex`对象时需要它。 指定您希望我们等一下，互斥体的名称和您的应用程序最初应拥有该域。 在构造函数将返回时，您就可以访问互斥体。 调用[CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock)完成后访问受控的资源。  
  
 一种方法来使用`CMutex`对象是添加类型的变量`CMutex`为您希望控件的类数据成员。 受控制的对象的构造，期间调用的构造函数`CMutex`指定是否互斥体为最初所拥有，互斥体 （如果它将用于跨进程边界） 的名称和所需的安全属性的数据成员。  
  
 通过控制访问资源`CMutex`对象以这种方式，先创建任一类型的变量[CSingleLock](../../mfc/reference/csinglelock-class.md)或类型[CMultiLock](../../mfc/reference/cmultilock-class.md)中资源的访问成员函数。 然后，调用的锁对象`Lock`成员函数 (例如， [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock))。 此时，您的线程将获得对资源的访问，等待被释放和获得访问权限，或等待要释放的资源和超时，无法访问该资源的资源。 在任何情况下，所需的资源已访问以线程安全的方式。 若要释放资源，使用的锁对象`Unlock`成员函数 (例如， [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock))，或允许离开作用域的锁对象。  
  
 有关详细信息使用`CMutex`对象，请参阅文章[多线程处理︰ 如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CMutex`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxmt.h  
  
##  <a name="a-namecmutexa--cmutexcmutex"></a><a name="cmutex"></a>CMutex::CMutex  
 构造的已命名的或未命名`CMutex`对象。  
  
```  
CMutex(
    BOOL bInitiallyOwn = FALSE,  
    LPCTSTR lpszName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```  
  
### <a name="parameters"></a>参数  
 `bInitiallyOwn`  
 如果指定线程创建`CMutex`对象最初具有对此互斥体控制资源的访问。  
  
 `lpszName`  
 `CMutex` 对象的名称。 如果存在具有相同名称的另一个互斥体，`lpszName`如果跨进程边界，将使用该对象必须提供。 如果**NULL**，将未命名的互斥体。 如果名称匹配现有的互斥体，该构造函数将生成新`CMutex`引用该名称的互斥体的对象。 如果名称与一个现有的同步对象，它不互斥体，构造将会失败。  
  
 `lpsaAttribute`  
 Mutex 对象的安全属性。 此结构的完整说明，请参阅[SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 若要访问或释放`CMutex`对象，请创建[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)对象，并调用其[锁](../../mfc/reference/csinglelock-class.md#lock)和[解锁](../../mfc/reference/csinglelock-class.md#unlock)成员函数。 如果`CMutex`对象使用独立，则调用其`Unlock`成员函数以将其释放。  
  
> [!IMPORTANT]
>  在创建后`CMutex`对象，请使用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)以确保，互斥体已不存在。 如果互斥体未存在意外，这可能表示一个恶意进程占用并可能想要出于恶意使用互斥体。 在这种情况下，建议的注重安全的过程是关闭句柄并继续像创建对象时出错。  
  
## <a name="see-also"></a>另请参阅  
 [CSyncObject 类](../../mfc/reference/csyncobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)




