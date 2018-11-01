---
title: CSyncObject 类
ms.date: 11/04/2016
f1_keywords:
- CSyncObject
- AFXMT/CSyncObject
- AFXMT/CSyncObject::CSyncObject
- AFXMT/CSyncObject::Lock
- AFXMT/CSyncObject::Unlock
- AFXMT/CSyncObject::m_hObject
helpviewer_keywords:
- CSyncObject [MFC], CSyncObject
- CSyncObject [MFC], Lock
- CSyncObject [MFC], Unlock
- CSyncObject [MFC], m_hObject
ms.assetid: c62ea6eb-a17b-4e01-aed4-321fc435a5f4
ms.openlocfilehash: d72d167be874d0776ce8da02784c2e0c267c9175
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547428"
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
|[CSyncObject::Lock](#lock)|提升访问同步对象。|
|[CSyncObject::Unlock](#unlock)|提升访问同步对象。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CSyncObject::operator 句柄](#operator_handle)|提供了对同步对象的访问。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CSyncObject::m_hObject](#m_hobject)|基础同步对象句柄。|

## <a name="remarks"></a>备注

Microsoft 基础类库提供了几个类派生自`CSyncObject`。 这些是[CEvent](../../mfc/reference/cevent-class.md)， [CMutex](../../mfc/reference/cmutex-class.md)， [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)，以及[CSemaphore](../../mfc/reference/csemaphore-class.md)。

有关如何使用同步对象的信息，请参阅文章[多线程处理： 如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CSyncObject`

## <a name="requirements"></a>要求

**标头：** afxmt.h

##  <a name="csyncobject"></a>  CSyncObject::CSyncObject

构造一个同步对象，使用提供的名称。

```
explicit CSyncObject(LPCTSTR pstrName);
virtual ~CSyncObject();
```

### <a name="parameters"></a>参数

*pstrName*<br/>
对象的名称。 如果为 NULL， *pstrName*将为 null。

##  <a name="lock"></a>  CSyncObject::Lock

调用此函数可获取对同步对象控制的资源的访问权限。

```
virtual BOOL Lock(DWORD dwTimeout = INFINITE);
```

### <a name="parameters"></a>参数

*dwTimeout*<br/>
指定的时间 （毫秒） 等待同步对象可用 （发出信号）。 如果无限期，`Lock`将等待，直到对象返回之前发出信号。

### <a name="return-value"></a>返回值

如果函数成功，则非零值否则为 0。

### <a name="remarks"></a>备注

如果同步对象发出信号，`Lock`将成功返回，并在线程现在拥有此对象。 如果同步对象是非终止状态 （不可用），`Lock`等待同步对象中指定的毫秒数目可高达收到信号*dwTimeOut*参数。 如果未收到同步对象信号中指定的时间内,`Lock`返回失败。

##  <a name="m_hobject"></a>  CSyncObject::m_hObject

基础同步对象句柄。

```
HANDLE m_hObject;
```

##  <a name="operator_handle"></a>  CSyncObject::operator 句柄

使用此运算符获取的句柄`CSyncObject`对象。

```
operator HANDLE() const;
```

### <a name="return-value"></a>返回值

如果成功，同步的对象; 的句柄否则，为 NULL。

### <a name="remarks"></a>备注

句柄可用于直接调用 Windows Api。

##  <a name="unlock"></a>  CSyncObject::Unlock

声明`Unlock`不带任何参数是一个纯虚函数，并且必须由派生自的所有类重写`CSyncObject`。

```
virtual BOOL Unlock() = 0; virtual BOOL Unlock(
    LONG lCount,
    LPLONG lpPrevCount = NULL);
```

### <a name="parameters"></a>参数

*lCount*<br/>
不使用默认实现。

*lpPrevCount*<br/>
不使用默认实现。

### <a name="return-value"></a>返回值

默认实现始终返回 TRUE。

### <a name="remarks"></a>备注

始终使用两个参数声明的默认实现，则返回 TRUE。 调用此函数以释放对由调用线程拥有同步对象的访问。 第二个声明提供同步对象，例如允许多个受控资源的访问的信号量。

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)

