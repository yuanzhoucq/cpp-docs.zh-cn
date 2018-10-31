---
title: CSingleLock 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CSingleLock [MFC], CSingleLock
- CSingleLock [MFC], IsLocked
- CSingleLock [MFC], Lock
- CSingleLock [MFC], Unlock
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 063ad23a9d356af0cac6c5b9dd8903e81530d2df
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061334"
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
|[CSingleLock::IsLocked](#islocked)|确定该对象被锁定。|
|[CSingleLock::Lock](#lock)|等待同步对象。|
|[CSingleLock::Unlock](#unlock)|释放同步对象。|

## <a name="remarks"></a>备注

`CSingleLock` 没有基类。

若要使用同步类[CSemaphore](../../mfc/reference/csemaphore-class.md)， [CMutex](../../mfc/reference/cmutex-class.md)， [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)，以及[CEvent](../../mfc/reference/cevent-class.md)，必须创建`CSingleLock`或[CMultiLock](../../mfc/reference/cmultilock-class.md)对象等待，并释放同步对象。 使用`CSingleLock`时只需等待上一个对象，一次。 使用`CMultiLock`时可以使用在特定时间的多个对象。

若要使用`CSingleLock`对象，请在受控的资源类中调用其构造函数内的成员函数。 然后调用[IsLocked](#islocked)成员函数以确定资源是否可用。 如果是，继续使用成员函数的其余部分。 如果资源不可用，等待指定的要释放的资源的时间内，或返回失败。 使用资源完成后，调用[解锁](#unlock)函数如果`CSingleLock`对象将再次，使用或允许`CSingleLock`要销毁对象。

`CSingleLock` 对象需要从派生的对象存在[CSyncObject](../../mfc/reference/csyncobject-class.md)。 这通常是类的受控的资源的数据成员。 有关如何使用的详细信息`CSingleLock`对象，请参阅文章[多线程处理： 如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CSingleLock`

## <a name="requirements"></a>要求

**标头：** afxmt.h

##  <a name="csinglelock"></a>  CSingleLock::CSingleLock

构造 `CSingleLock` 对象。

```
explicit CSingleLock(
    CSyncObject* pObject,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>参数

*pObject*<br/>
指向要访问的同步对象。 不能为 NULL。

*bInitialLock*<br/>
指定是否以最初尝试访问所提供的对象。

### <a name="remarks"></a>备注

此函数通常是从受控资源的访问成员函数中调用的。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#19](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]

##  <a name="islocked"></a>  CSingleLock::IsLocked

确定是否对象与关联`CSingleLock`对象是非终止状态 （不可用）。

```
BOOL IsLocked();
```

### <a name="return-value"></a>返回值

如果对象被锁定，则非零值否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#20](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]

##  <a name="lock"></a>  CSingleLock::Lock

调用此函数可对由提供给的同步对象控制资源访问`CSingleLock`构造函数。

```
BOOL Lock(DWORD dwTimeOut = INFINITE);
```

### <a name="parameters"></a>参数

*dwTimeOut*<br/>
指定的时间来等待同步对象可用 （发出信号）。 如果无限期，`Lock`将等待，直到对象返回之前发出信号。

### <a name="return-value"></a>返回值

如果函数成功，则非零值否则为 0。

### <a name="remarks"></a>备注

如果同步对象发出信号，`Lock`将成功返回，并在线程现在拥有此对象。 如果同步对象是非终止状态 （不可用），`Lock`等待同步对象中指定的毫秒数目可高达收到信号*dwTimeOut*参数。 如果未收到同步对象信号中指定的时间内,`Lock`返回失败。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

##  <a name="unlock"></a>  CSingleLock::Unlock

释放所拥有的同步对象`CSingleLock`。

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>参数

*lCount*<br/>
若要释放的访问次数。 必须大于 0。 如果指定的量将导致超过其最大值的对象计数，计数不会更改，并且该函数将返回 FALSE。

*lPrevCount*<br/>
指向一个变量来接收的同步对象的前一个计数。 如果为 NULL，则不返回前一个计数。

### <a name="return-value"></a>返回值

如果函数成功，则非零值否则为 0。

### <a name="remarks"></a>备注

调用此函数`CSingleLock`的析构函数。

如果你需要释放信号量的多个访问计数，使用的第二种形式`Unlock`并指定要发布的访问次数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CMultiLock 类](../../mfc/reference/cmultilock-class.md)
