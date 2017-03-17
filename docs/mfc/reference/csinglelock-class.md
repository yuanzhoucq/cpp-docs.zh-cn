---
title: "CSingleLock 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSingleLock
- AFXMT/CSingleLock
- AFXMT/CSingleLock::CSingleLock
- AFXMT/CSingleLock::IsLocked
- AFXMT/CSingleLock::Lock
- AFXMT/CSingleLock::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CSingleLock class
- threading [MFC], access control
- synchronization objects, access control
- threading [MFC], synchronization
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
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
ms.openlocfilehash: b1efc2daf1c3714446223cc69f9cc2a6a3401173
ms.lasthandoff: 02/24/2017

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
  
|名称|说明|  
|----------|-----------------|  
|[CSingleLock::IsLocked](#islocked)|确定对象被锁定。|  
|[CSingleLock::Lock](#lock)|在同步对象中等待。|  
|[CSingleLock::Unlock](#unlock)|释放同步对象。|  
  
## <a name="remarks"></a>备注  
 `CSingleLock`没有基类的类。  
  
 若要使用同步类[CSemaphore](../../mfc/reference/csemaphore-class.md)， [CMutex](../../mfc/reference/cmutex-class.md)， [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)，和[CEvent](../../mfc/reference/cevent-class.md)，您必须创建`CSingleLock`或[CMultiLock](../../mfc/reference/cmultilock-class.md)对象等待，并释放同步对象。 使用`CSingleLock`时只需一次针对一个对象的等待。 使用**CMultiLock**时有多个可以使用某一时刻的对象。  
  
 若要使用`CSingleLock`对象，请在受控的资源的类中调用其构造函数在成员函数内的。 然后，调用[IsLocked](#islocked)成员函数来确定该资源是否可用。 如果是，继续使用该成员函数的其余部分。 如果该资源不可用，等待指定的资源要释放的时间量，或返回失败。 使用该资源已完成后，或者调用[解锁](#unlock)函数如果`CSingleLock`对象是同样，使用或允许`CSingleLock`对象将其销毁。  
  
 `CSingleLock`对象需要将一个对象派生自存在[CSyncObject](../../mfc/reference/csyncobject-class.md)。 这通常是受控的资源类的数据成员。 有关如何使用`CSingleLock`对象，请参阅文章[多线程处理︰ 如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CSingleLock`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxmt.h  
  
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
 [!code-cpp[NVC_MFC_Utilities #&19;](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]  
  
##  <a name="islocked"></a>CSingleLock::IsLocked  
 确定是否对象与关联`CSingleLock`对象是非终止状态 （不可用）。  
  
```  
BOOL IsLocked();
```  
  
### <a name="return-value"></a>返回值  
 如果该对象被锁定，则非零值否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities #&20;](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]  
  
##  <a name="lock"></a>CSingleLock::Lock  
 调用此函数可获取对由提供给的同步对象控制的资源访问权限`CSingleLock`构造函数。  
  
```  
BOOL Lock(DWORD dwTimeOut = INFINITE);
```  
  
### <a name="parameters"></a>参数  
 *dwTimeOut*  
 指定要等待同步对象可用的时间量 （终止）。 如果**无限**，`Lock`将等待，直到在返回之前，该对象处于终止状态。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 如果同步对象发出信号，`Lock`将立即成功返回，并在线程现在拥有对象。 如果同步对象是非终止状态 （不可用）`Lock`将等待要接收信号最中指定的毫秒数的同步对象*dwTimeOut*参数。 如果没有未在指定的时间量，接收信号的同步对象`Lock`返回失败。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities #&21;](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]  
  
##  <a name="unlock"></a>CSingleLock::Unlock  
 释放同步对象归`CSingleLock`。  
  
```  
BOOL Unlock();

 
BOOL Unlock(
    LONG lCount,  
    LPLONG lPrevCount = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lCount`  
 若要释放的访问次数。 必须大于 0。 如果指定的量会导致对象的计数超出其最大值，计数未发生更改时，该函数将返回**FALSE**。  
  
 `lPrevCount`  
 指向一个变量来接收的同步对象的前一个计数。 如果**NULL**，则不返回前一个计数。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此函数`CSingleLock`的析构函数。  
  
 如果你需要释放信号量的多个访问次数，使用第二种形式的`Unlock`并指定要发布的访问次数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities #&21;](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CMultiLock 类](../../mfc/reference/cmultilock-class.md)

