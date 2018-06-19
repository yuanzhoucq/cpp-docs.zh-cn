---
title: CSyncObject 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSyncObject
- AFXMT/CSyncObject
- AFXMT/CSyncObject::CSyncObject
- AFXMT/CSyncObject::Lock
- AFXMT/CSyncObject::Unlock
- AFXMT/CSyncObject::m_hObject
dev_langs:
- C++
helpviewer_keywords:
- CSyncObject [MFC], CSyncObject
- CSyncObject [MFC], Lock
- CSyncObject [MFC], Unlock
- CSyncObject [MFC], m_hObject
ms.assetid: c62ea6eb-a17b-4e01-aed4-321fc435a5f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1712f0d26fc0d9ac3dcfb0f2a15a906351f43154
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374092"
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
  
|名称|描述|  
|----------|-----------------|  
|[CSyncObject::Lock](#lock)|提升到的同步对象的访问。|  
|[CSyncObject::Unlock](#unlock)|提升到的同步对象的访问。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CSyncObject::operator 句柄](#operator_handle)|提供对同步对象的访问。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CSyncObject::m_hObject](#m_hobject)|基础的同步对象句柄。|  
  
## <a name="remarks"></a>备注  
 Microsoft 基础类库提供了几个类派生自`CSyncObject`。 这些是[CEvent](../../mfc/reference/cevent-class.md)， [CMutex](../../mfc/reference/cmutex-class.md)， [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)，和[CSemaphore](../../mfc/reference/csemaphore-class.md)。  
  
 有关如何使用同步对象的信息，请参阅文章[多线程处理： 如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CSyncObject`  
  
## <a name="requirements"></a>要求  
 **标头：** afxmt.h  
  
##  <a name="csyncobject"></a>  CSyncObject::CSyncObject  
 构造具有提供的名称的同步对象。  
  
```  
explicit CSyncObject(LPCTSTR pstrName);  
virtual ~CSyncObject();
```  
  
### <a name="parameters"></a>参数  
 `pstrName`  
 对象的名称。 如果**NULL**， *pstrName*将为 null。  
  
##  <a name="lock"></a>  CSyncObject::Lock  
 调用此函数可获取对由同步对象控制资源访问权限。  
  
```  
virtual BOOL Lock(DWORD dwTimeout = INFINITE);
```  
  
### <a name="parameters"></a>参数  
 `dwTimeout`  
 指定的时间 （毫秒） 等待同步对象可用 （发出信号）。 如果**无限**，`Lock`将等待，直到该对象在返回之前处于有信号状态。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则为 0。  
  
### <a name="remarks"></a>备注  
 如果同步对象发出信号，`Lock`将成功返回，并在线程现在拥有对象。 如果同步对象是非终止状态 （不可用），`Lock`将等待同步对象中指定的毫秒数最变为终止状态*dwTimeOut*参数。 如果同步对象未不会变得收到信号的状态的时间，指定的量`Lock`返回失败。  
  
##  <a name="m_hobject"></a>  CSyncObject::m_hObject  
 基础的同步对象句柄。  
  
```  
HANDLE m_hObject;  
```  
  
##  <a name="operator_handle"></a>  CSyncObject::operator 句柄  
 使用此运算符来获取的句柄`CSyncObject`对象。  
  
```  
operator HANDLE() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，同步对象中; 的句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 句柄可用于直接调用 Windows Api。  
  
##  <a name="unlock"></a>  CSyncObject::Unlock  
 声明`Unlock`不带任何参数纯虚拟函数，并且必须由所有派生自的类中重写`CSyncObject`。  
  
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
 两个参数的声明始终的默认实现返回**TRUE**。 调用此函数以释放拥有由调用线程的同步对象访问权限。 第二个声明进行同步的对象，如允许的受控资源的多个访问的信号量。  
  
## <a name="see-also"></a>请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)



