---
title: "CSyncObject 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSyncObject
dev_langs:
- C++
helpviewer_keywords:
- CSyncObject class
- synchronization classes, CSyncObject
ms.assetid: c62ea6eb-a17b-4e01-aed4-321fc435a5f4
caps.latest.revision: 21
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a1f0c8ddfbfaf129bb18c14d36b998dd37d35899
ms.lasthandoff: 02/24/2017

---
# <a name="csyncobject-class"></a>CSyncObject 类
一个纯虚拟类，提供 Win32 中的同步对象所共有的功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CSyncObject : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CSyncObject::CSyncObject](#csyncobject)|构造 `CSyncObject` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CSyncObject::Lock](#lock)|提高对同步对象的访问。|  
|[CSyncObject::Unlock](#unlock)|提高对同步对象的访问。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CSyncObject::operator 句柄](#operator_handle)|提供对同步对象的访问。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CSyncObject::m_hObject](#m_hobject)|基础同步对象的句柄。|  
  
## <a name="remarks"></a>备注  
 Microsoft 基础类库提供了几个类派生自`CSyncObject`。 这些是[CEvent](../../mfc/reference/cevent-class.md)， [CMutex](../../mfc/reference/cmutex-class.md)， [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)，和[CSemaphore](../../mfc/reference/csemaphore-class.md)。  
  
 有关如何使用同步对象的信息，请参阅文章[多线程处理︰ 如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CSyncObject`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxmt.h  
  
##  <a name="a-namecsyncobjecta--csyncobjectcsyncobject"></a><a name="csyncobject"></a>CSyncObject::CSyncObject  
 构造使用提供的名称的同步对象。  
  
```  
explicit CSyncObject(LPCTSTR pstrName);  
virtual ~CSyncObject();
```  
  
### <a name="parameters"></a>参数  
 `pstrName`  
 对象的名称。 如果**NULL**， *pstrName*将为 null。  
  
##  <a name="a-namelocka--csyncobjectlock"></a><a name="lock"></a>CSyncObject::Lock  
 调用此函数可获取对同步对象控制的资源访问权限。  
  
```  
virtual BOOL Lock(DWORD dwTimeout = INFINITE);
```  
  
### <a name="parameters"></a>参数  
 `dwTimeout`  
 指定的时间量 （毫秒） 等待同步对象可用 （终止）。 如果**无限**，`Lock`将等待，直到在返回之前，该对象处于终止状态。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 如果同步对象发出信号，`Lock`将立即成功返回，并在线程现在拥有对象。 如果同步对象是非终止状态 （不可用）`Lock`将等待要接收信号最中指定的毫秒数的同步对象*dwTimeOut*参数。 如果没有未在指定的时间量，接收信号的同步对象`Lock`返回失败。  
  
##  <a name="a-namemhobjecta--csyncobjectmhobject"></a><a name="m_hobject"></a>CSyncObject::m_hObject  
 基础同步对象的句柄。  
  
```  
HANDLE m_hObject;  
```  
  
##  <a name="a-nameoperatorhandlea--csyncobjectoperator-handle"></a><a name="operator_handle"></a>CSyncObject::operator 句柄  
 使用此运算符将获取的句柄`CSyncObject`对象。  
  
```  
operator HANDLE() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，同步对象中; 的句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 该句柄可用于直接调用 Windows Api。  
  
##  <a name="a-nameunlocka--csyncobjectunlock"></a><a name="unlock"></a>CSyncObject::Unlock  
 声明`Unlock`不带任何参数是一个纯虚拟函数，并且必须由派生自的所有类重写`CSyncObject`。  
  
```  
virtual BOOL Unlock() = 0; virtual BOOL Unlock(
    LONG lCount,  
    LPLONG lpPrevCount = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lCount`  
 不使用默认实现。  
  
 `lpPrevCount`  
 不使用默认实现。  
  
### <a name="return-value"></a>返回值  
 默认实现始终返回**TRUE**。  
  
### <a name="remarks"></a>备注  
 始终用两个参数声明的默认实现返回**TRUE**。 调用此函数来释放给调用线程所拥有的同步对象的访问。 第二个声明用于如允许多个受控资源的访问的信号量同步对象。  
  
## <a name="see-also"></a>另请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)




