---
title: "CSingleLock 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSingleLock
- AFXMT/CSingleLock
- AFXMT/CSingleLock::CSingleLock
- AFXMT/CSingleLock::IsLocked
- AFXMT/CSingleLock::Lock
- AFXMT/CSingleLock::Unlock
dev_langs: C++
helpviewer_keywords:
- CSingleLock [MFC], CSingleLock
- CSingleLock [MFC], IsLocked
- CSingleLock [MFC], Lock
- CSingleLock [MFC], Unlock
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0dd07d79c97a9fb3368d20ee68df2332ba7ce5cf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="csinglelock-class"></a>CSingleLock 类
表示多线程程序中用于控制对一个资源的访问的访问控制机制。  
  
## <a name="syntax"></a>语法  
  
```  
class CSingleLock  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CSingleLock::CSingleLock](#csinglelock)|构造 `CSingleLock` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSingleLock::IsLocked](#islocked)|确定对象被锁定。|  
|[CSingleLock::Lock](#lock)|等待同步对象。|  
|[CSingleLock::Unlock](#unlock)|释放的同步对象。|  
  
## <a name="remarks"></a>备注  
 `CSingleLock`没有基类。  
  
 若要使用同步类[CSemaphore](../../mfc/reference/csemaphore-class.md)， [CMutex](../../mfc/reference/cmutex-class.md)， [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)，和[CEvent](../../mfc/reference/cevent-class.md)，你必须创建`CSingleLock`或[CMultiLock](../../mfc/reference/cmultilock-class.md)等待并释放同步对象的对象。 使用`CSingleLock`时只需一次等待上一个对象。 使用**CMultiLock**时有多个对象，你无法使用在特定的时间。  
  
 若要使用`CSingleLock`对象，请在受控的资源类中调用其构造函数内的成员函数。 然后调用[IsLocked](#islocked)成员函数来确定该资源是否可用。 如果是，继续而成员函数的其余部分。 如果资源不可用，则等待指定数量的资源要释放的时间，或返回失败。 使用的资源已完成后，请调用[解锁](#unlock)函数如果`CSingleLock`对象是同样，使用或允许`CSingleLock`对象将其销毁。  
  
 `CSingleLock`对象需要将派生自的对象是否存在[CSyncObject](../../mfc/reference/csyncobject-class.md)。 这通常是类的受控的资源的数据成员。 有关详细信息如何使用`CSingleLock`对象，请参阅文章[多线程处理： 如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CSingleLock`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxmt.h  
  
##  <a name="csinglelock"></a>CSingleLock::CSingleLock  
 构造 `CSingleLock` 对象。  
  
```  
explicit CSingleLock(
    CSyncObject* pObject,  
    BOOL bInitialLock = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `pObject`  
 指向要访问的同步对象。 不能为**NULL**。  
  
 `bInitialLock`  
 指定是否以最初尝试访问所提供的对象。  
  
### <a name="remarks"></a>备注  
 此函数通常是从受控资源的访问成员函数中调用的。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities#19](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]  
  
##  <a name="islocked"></a>CSingleLock::IsLocked  
 确定与相关的对象是否`CSingleLock`对象是非终止状态 （不可用）。  
  
```  
BOOL IsLocked();
```  
  
### <a name="return-value"></a>返回值  
 如果对象被锁定; 则为非 0否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities#20](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]  
  
##  <a name="lock"></a>CSingleLock::Lock  
 调用此函数可获取对由提供给的同步对象控制资源访问权限`CSingleLock`构造函数。  
  
```  
BOOL Lock(DWORD dwTimeOut = INFINITE);
```  
  
### <a name="parameters"></a>参数  
 *dwTimeOut*  
 指定要等待同步对象可用的时间量 （发出信号）。 如果**无限**，`Lock`将等待，直到该对象在返回之前处于有信号状态。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则为 0。  
  
### <a name="remarks"></a>备注  
 如果同步对象发出信号，`Lock`将成功返回，并在线程现在拥有对象。 如果同步对象是非终止状态 （不可用），`Lock`将等待同步对象中指定的毫秒数最变为终止状态*dwTimeOut*参数。 如果同步对象未不会变得收到信号的状态的时间，指定的量`Lock`返回失败。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]  
  
##  <a name="unlock"></a>CSingleLock::Unlock  
 释放所拥有的同步对象`CSingleLock`。  
  
```  
BOOL Unlock();

 
BOOL Unlock(
    LONG lCount,  
    LPLONG lPrevCount = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lCount`  
 若要释放的访问次数。 必须大于 0。 如果指定的量将导致超过其最大值的对象的计数，计数未发生更改，并且该函数将返回**FALSE**。  
  
 `lPrevCount`  
 指向要接收同步对象的前一个计数的变量。 如果**NULL**，则不返回前一个计数。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此函数`CSingleLock`的析构函数。  
  
 如果你需要时常释放信号量的多个访问次数，使用的第二种形式`Unlock`和指定的访问以释放次数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CMultiLock 类](../../mfc/reference/cmultilock-class.md)
