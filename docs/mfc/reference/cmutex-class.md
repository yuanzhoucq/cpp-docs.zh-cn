---
title: CMutex 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMutex
- AFXMT/CMutex
- AFXMT/CMutex::CMutex
dev_langs:
- C++
helpviewer_keywords:
- CMutex [MFC], CMutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50d2d68aedaf1d5560c39971e9dd5f74b4492ac6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372455"
---
# <a name="cmutex-class"></a>CMutex 类
表示一个"互斥体"-允许一个线程互相排斥的方式访问资源的同步对象。  
  
## <a name="syntax"></a>语法  
  
```  
class CMutex : public CSyncObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMutex::CMutex](#cmutex)|构造 `CMutex` 对象。|  
  
## <a name="remarks"></a>备注  
 当一次只有一个线程可以有权修改数据或某个其他受控的资源，互斥体非常有用。 例如，如果将节点添加到链接的列表中，则是应仅允许一个线程通过一次一个过程。 通过使用`CMutex`对象以控制链接的列表中，仅一次一个线程可以获得对列表的访问。  
  
 若要使用`CMutex`对象，构造`CMutex`对象时需要它。 指定你想要等待，互斥体的名称和你的应用程序最初应拥有它。 然后，在构造函数将返回时，就可以访问互斥体。 调用[CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock)完成后访问受控的资源。  
  
 一种方法来使用`CMutex`对象是添加类型的变量的`CMutex`为想要控制的类数据成员。 在受控的对象的构造，过程调用的构造函数`CMutex`指定是否互斥体最初拥有、 互斥体 （如果跨进程边界，将使用它） 的名称和所需的安全属性的数据成员。  
  
 由控制访问资源`CMutex`对象以这种方式，先创建任一类型的变量的[CSingleLock](../../mfc/reference/csinglelock-class.md)或类型[CMultiLock](../../mfc/reference/cmultilock-class.md)中资源的访问成员函数。 然后，调用的锁对象`Lock`成员函数 (例如， [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock))。 此时，你的线程将获取对资源的访问，等待要释放并获取访问权限，或者等待的资源要释放和超时值，不能对资源的访问的资源。 在任何情况下，所需的资源已被访问以线程安全的方式。 若要释放资源，使用的锁对象`Unlock`成员函数 (例如， [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock))，或允许未能超出范围的锁对象。  
  
 有关详细信息使用`CMutex`对象，请参阅文章[多线程处理： 如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CMutex`  
  
## <a name="requirements"></a>要求  
 **标头：** afxmt.h  
  
##  <a name="cmutex"></a>  CMutex::CMutex  
 命名的或未命名的构造`CMutex`对象。  
  
```  
CMutex(
    BOOL bInitiallyOwn = FALSE,  
    LPCTSTR lpszName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```  
  
### <a name="parameters"></a>参数  
 `bInitiallyOwn`  
 指定如果线程创建`CMutex`对象最初具有由互斥体控制资源访问权限。  
  
 `lpszName`  
 `CMutex` 对象的名称。 如果存在具有相同名称的另一个互斥体，`lpszName`如果跨进程边界，将使用该对象必须提供。 如果**NULL**，将未命名互斥体。 如果名称与匹配现有的互斥体，构造函数将生成新`CMutex`即在引用该名称的互斥体的对象。 如果名称与匹配现有同步对象不是一个 mutex，构造将失败。  
  
 `lpsaAttribute`  
 Mutex 对象的安全属性。 此结构的完整说明，请参阅[SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) Windows SDK 中。  
  
### <a name="remarks"></a>备注  
 若要访问或释放`CMutex`对象，请创建[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)对象并调用其[锁](../../mfc/reference/csinglelock-class.md#lock)和[解锁](../../mfc/reference/csinglelock-class.md#unlock)成员函数。 如果`CMutex`对象正在使用独立，调用其`Unlock`成员函数以将其释放。  
  
> [!IMPORTANT]
>  在创建后`CMutex`对象，请使用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)以确保，互斥体已不存在。 如果互斥体未意外存在，则可能表示一个恶意进程是占用和可能想要恶意使用互斥体。 在这种情况下，建议的安全意识过程是关闭句柄并继续就像在创建对象时失败。  
  
## <a name="see-also"></a>请参阅  
 [CSyncObject 类](../../mfc/reference/csyncobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)



