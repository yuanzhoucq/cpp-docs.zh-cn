---
title: CSync对象类
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
ms.openlocfilehash: ebfbc185cdca2effc96ce2e6d96d05f997c52bf7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365975"
---
# <a name="csyncobject-class"></a>CSync对象类

一个纯虚拟类，提供 Win32 中的同步对象所共有的功能。

## <a name="syntax"></a>语法

```
class CSyncObject : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CSync对象：CSync对象](#csyncobject)|构造 `CSyncObject` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CSync对象：锁定](#lock)|获得对同步对象的访问权限。|
|[CSync对象：解锁](#unlock)|获得对同步对象的访问权限。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CSync对象：：操作员HANDLE](#operator_handle)|提供对同步对象的访问。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CSync对象：m_hObject](#m_hobject)|基础同步对象的句柄。|

## <a name="remarks"></a>备注

Microsoft 基础类库提供来自`CSyncObject`的多个类。 这些是[CEvent，CMutex，C](../../mfc/reference/cmutex-class.md)[临界截面](../../mfc/reference/ccriticalsection-class.md)，和[CSemaphore。](../../mfc/reference/csemaphore-class.md) [CEvent](../../mfc/reference/cevent-class.md)

有关如何使用同步对象的信息，请参阅"[多线程：如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)"一文。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CSyncObject`

## <a name="requirements"></a>要求

**标题：** afxmt.h

## <a name="csyncobjectcsyncobject"></a><a name="csyncobject"></a>CSync对象：CSync对象

构造具有提供名称的同步对象。

```
explicit CSyncObject(LPCTSTR pstrName);
virtual ~CSyncObject();
```

### <a name="parameters"></a>参数

*pstrName*<br/>
对象的名称。 如果为 NULL，*则 pstrName*将为空。

## <a name="csyncobjectlock"></a><a name="lock"></a>CSync对象：锁定

调用此函数以访问由同步对象控制的资源。

```
virtual BOOL Lock(DWORD dwTimeout = INFINITE);
```

### <a name="parameters"></a>参数

*dwTimeout*<br/>
指定等待同步对象可用（信号）的时间量（以毫秒为单位）。 如果 INFINITE，`Lock`将等待对象发出信号后再返回。

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0。

### <a name="remarks"></a>备注

如果同步对象发出信号，`Lock`将成功返回，并且线程现在拥有该对象。 如果同步对象是非信号（不可用），`Lock`则将等待同步对象发出信号，最多达到*dwTimeOut*参数中指定的毫秒数。 如果同步对象未在指定的时间内发出信号，则`Lock`返回失败。

## <a name="csyncobjectm_hobject"></a><a name="m_hobject"></a>CSync对象：m_hObject

基础同步对象的句柄。

```
HANDLE m_hObject;
```

## <a name="csyncobjectoperator-handle"></a><a name="operator_handle"></a>CSync对象：：操作员HANDLE

使用此运算符获取`CSyncObject`对象的句柄。

```
operator HANDLE() const;
```

### <a name="return-value"></a>返回值

如果成功，则处理同步对象的句柄;否则，NULL。

### <a name="remarks"></a>备注

您可以使用该句柄直接调用 Windows API。

## <a name="csyncobjectunlock"></a><a name="unlock"></a>CSync对象：解锁

`Unlock`无参数的声明是纯虚拟函数，必须由派生自`CSyncObject`的所有类重写。

```
virtual BOOL Unlock() = 0; virtual BOOL Unlock(
    LONG lCount,
    LPLONG lpPrevCount = NULL);
```

### <a name="parameters"></a>参数

*lCount*<br/>
默认情况下不使用实现。

*lpPrevCount*<br/>
默认情况下不使用实现。

### <a name="return-value"></a>返回值

默认实现始终返回 TRUE。

### <a name="remarks"></a>备注

具有两个参数的声明的默认实现始终返回 TRUE。 调用此函数是为了释放对调用线程拥有的同步对象的访问。 第二个声明用于同步对象，如允许对受控资源的多个访问权限的信号量。

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
