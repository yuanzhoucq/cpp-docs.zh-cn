---
title: C信号器类
ms.date: 11/04/2016
f1_keywords:
- CSemaphore
- AFXMT/CSemaphore
- AFXMT/CSemaphore::CSemaphore
helpviewer_keywords:
- CSemaphore [MFC], CSemaphore
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
ms.openlocfilehash: 26e1fd55d321b221f4732874d57d02a79c4c6398
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318499"
---
# <a name="csemaphore-class"></a>C信号器类

类`CSemaphore`的对象表示"信号量"，即允许一个或多个进程中有限数量的线程访问维护当前访问指定资源的线程数的同步对象。

## <a name="syntax"></a>语法

```
class CSemaphore : public CSyncObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CSemaphore：CSemaphore](#csemaphore)|构造 `CSemaphore` 对象。|

## <a name="remarks"></a>备注

Semaphores 在控制对只能支持有限数量的用户的共享资源的访问方面非常有用。 `CSemaphore`对象的当前计数是允许的其他用户数。 当计数达到零时，所有尝试使用`CSemaphore`对象控制的资源的尝试都将插入到系统队列中，并等待超时或计数上升到 0 以上。 在构建`CSemaphore`对象期间，指定一次可以访问受控资源的最大用户数。

要使用`CSemaphore`对象，`CSemaphore`在需要对象时构造该对象。 指定要等待的信号量的名称，并且应用程序最初应拥有它。 然后，当构造函数返回时，可以访问信号量。 调用[CSyncObject：：访问](../../mfc/reference/csyncobject-class.md#unlock)受控资源后解锁。

使用`CSemaphore`对象的替代方法是将类型的`CSemaphore`变量作为数据成员添加到要控制的类中。 在构造受控对象期间，调用`CSemaphore`数据成员的构造函数，指定初始访问计数、最大访问计数、信号量的名称（如果它将跨进程边界使用）和所需的安全属性。

要以这种方式访问受`CSemaphore`对象控制的资源，请首先在资源的访问成员函数中创建[CSingleLock](../../mfc/reference/csinglelock-class.md)类型或[CMultiLock](../../mfc/reference/cmultilock-class.md)类型的变量。 然后调用锁对象`Lock`的成员函数（例如[，CSingleLock：：锁定](../../mfc/reference/csinglelock-class.md#lock)）。 此时，线程将获取对资源的访问，等待资源被释放并获取访问权限，或者等待资源释放和超时，无法访问资源。 在任何情况下，您的资源都以线程安全的方式访问。 要释放资源，请使用锁定对象`Unlock`的成员函数（例如[，CSingleLock：：解锁](../../mfc/reference/csinglelock-class.md#unlock)），或允许锁定对象退出范围。

或者，您可以创建独立`CSemaphore`对象，并在尝试访问受控资源之前显式访问它。 此方法虽然对读取源代码的人更清晰，但更容易出错。

有关如何使用`CSemaphore`对象的详细信息，请参阅"[多线程：如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)"一文。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CSemaphore`

## <a name="requirements"></a>要求

**标题：** afxmt.h

## <a name="csemaphorecsemaphore"></a><a name="csemaphore"></a>CSemaphore：CSemaphore

构造命名或未命名`CSemaphore`的对象。

```
CSemaphore(
    LONG lInitialCount = 1,
    LONG lMaxCount = 1,
    LPCTSTR pstrName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```

### <a name="parameters"></a>参数

*l 初始计数*<br/>
信号量的初始使用计数。 必须大于或等于 0，小于或等于*lMaxCount*。

*lMaxCount*<br/>
信号量的最大使用计数。 必须大于 0。

*pstrName*<br/>
信号量的名称。 如果信号量将跨进程边界访问，则必须提供信号量。 如果`NULL`，对象将未命名。 如果名称与现有信号量匹配，构造函数将生成一个新`CSemaphore`对象，引用该名称的信号量。 如果名称与现有不是信号量的同步对象匹配，则构造将失败。

*lpsa属性*<br/>
信号量对象的安全属性。 有关此结构的完整说明，请参阅 Windows SDK 中的[SECURITY_ATTRIBUTES。](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))

### <a name="remarks"></a>备注

要访问或`CSemaphore`释放对象，请创建[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)对象，并调用其[锁定](../../mfc/reference/csinglelock-class.md#lock)和[解锁](../../mfc/reference/csinglelock-class.md#unlock)成员函数。

> [!IMPORTANT]
> 创建对象后`CSemaphore`，请使用[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)确保互斥体不存在。 如果互斥体确实意外存在，则可能表示恶意进程正在蹲下，并且可能打算恶意使用互斥体。 在这种情况下，建议的安全意识过程是关闭句柄并继续，就像创建对象时失败一样。

## <a name="see-also"></a>另请参阅

[CSync对象类](../../mfc/reference/csyncobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
