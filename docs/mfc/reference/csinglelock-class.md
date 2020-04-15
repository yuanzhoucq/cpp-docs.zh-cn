---
title: 单锁类
ms.date: 11/04/2016
f1_keywords:
- CSingleLock
- AFXMT/CSingleLock
- AFXMT/CSingleLock::CSingleLock
- AFXMT/CSingleLock::IsLocked
- AFXMT/CSingleLock::Lock
- AFXMT/CSingleLock::Unlock
helpviewer_keywords:
- CSingleLock [MFC], CSingleLock
- CSingleLock [MFC], IsLocked
- CSingleLock [MFC], Lock
- CSingleLock [MFC], Unlock
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
ms.openlocfilehash: 231397228d94e58665602453b5d377571e24a967
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318274"
---
# <a name="csinglelock-class"></a>单锁类

表示多线程程序中用于控制对一个资源的访问的访问控制机制。

## <a name="syntax"></a>语法

```
class CSingleLock
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[单一锁：C单锁](#csinglelock)|构造 `CSingleLock` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[单一锁定：锁定](#islocked)|确定对象是否锁定。|
|[单锁：锁定](#lock)|在同步对象上等待。|
|[单锁：解锁](#unlock)|释放同步对象。|

## <a name="remarks"></a>备注

`CSingleLock`没有基类。

为了使用同步类[CSemaphore、CMutex、C](../../mfc/reference/csemaphore-class.md)[关键节](../../mfc/reference/ccriticalsection-class.md)和[CEvent，](../../mfc/reference/cevent-class.md)必须创建一个`CSingleLock`或[CMultiLock](../../mfc/reference/cmultilock-class.md)对象来等待并释放同步对象。 [CMutex](../../mfc/reference/cmutex-class.md) 在`CSingleLock`一次只需等待一个对象时使用。 `CMultiLock`当在特定时间可以使用多个对象时使用。

要使用`CSingleLock`对象，请将其构造函数调用受控资源类中的成员函数内。 然后调用[IsLocked](#islocked)成员函数以确定资源是否可用。 如果是，请继续执行成员函数的其余部分。 如果资源不可用，请等待指定的时间量以释放资源，或返回失败。 资源使用完成后，如果要再次使用该对象，[Unlock](#unlock)`CSingleLock`则调用 Unlock 函数，或者允许销毁`CSingleLock`该对象。

`CSingleLock`对象需要存在从[CSyncObject](../../mfc/reference/csyncobject-class.md)派生的对象。 这通常是受控资源类的数据成员。 有关如何使用`CSingleLock`对象的详细信息，请参阅"[多线程：如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)"一文。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CSingleLock`

## <a name="requirements"></a>要求

**标题：** afxmt.h

## <a name="csinglelockcsinglelock"></a><a name="csinglelock"></a>单一锁：C单锁

构造 `CSingleLock` 对象。

```
explicit CSingleLock(
    CSyncObject* pObject,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>参数

*pObject*<br/>
指向要访问的同步对象。 不能为 NULL。

*b 初始锁定*<br/>
指定是否最初尝试访问提供的对象。

### <a name="remarks"></a>备注

此函数通常从受控资源的访问成员函数内调用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#19](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]

## <a name="csinglelockislocked"></a><a name="islocked"></a>单一锁定：锁定

确定与`CSingleLock`对象关联的对象是否非信号（不可用）。

```
BOOL IsLocked();
```

### <a name="return-value"></a>返回值

如果对象已锁定，则非零;否则 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#20](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]

## <a name="csinglelocklock"></a><a name="lock"></a>单锁：锁定

调用此函数以访问由提供给`CSingleLock`构造函数的同步对象控制的资源。

```
BOOL Lock(DWORD dwTimeOut = INFINITE);
```

### <a name="parameters"></a>参数

*dwTimeOut*<br/>
指定等待同步对象可用（信号）的时间量。 如果 INFINITE，`Lock`将等待对象发出信号后再返回。

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0。

### <a name="remarks"></a>备注

如果同步对象发出信号，`Lock`将成功返回，并且线程现在拥有该对象。 如果同步对象是非信号（不可用），`Lock`则将等待同步对象发出信号，最多达到*dwTimeOut*参数中指定的毫秒数。 如果同步对象未在指定的时间内发出信号，则`Lock`返回失败。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="csinglelockunlock"></a><a name="unlock"></a>单锁：解锁

释放 拥有的`CSingleLock`同步对象。

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>参数

*lCount*<br/>
要释放的访问数。 必须大于 0。 如果指定量将导致对象的计数超过其最大值，则计数不会更改，并且函数将返回 FALSE。

*lPrevCount*<br/>
指向变量以接收同步对象的上一个计数。 如果为 NULL，则不返回以前的计数。

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0。

### <a name="remarks"></a>备注

此函数由`CSingleLock`析构函数调用。

如果需要释放信号量的多个访问计数，请使用 第`Unlock`二种形式并指定要释放的访问数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[C 多锁类](../../mfc/reference/cmultilock-class.md)
