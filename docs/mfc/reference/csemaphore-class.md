---
title: CSemaphore 类
ms.date: 11/04/2016
f1_keywords:
- CSemaphore
- AFXMT/CSemaphore
- AFXMT/CSemaphore::CSemaphore
helpviewer_keywords:
- CSemaphore [MFC], CSemaphore
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
ms.openlocfilehash: d5a0e4187107aaab7cedf4e7a0e2fc47b9f9f305
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502584"
---
# <a name="csemaphore-class"></a>CSemaphore 类

类`CSemaphore`的对象表示一个 "信号量"-一种同步对象, 允许一个或多个进程中有限数量的线程访问指定资源的线程数。

## <a name="syntax"></a>语法

```
class CSemaphore : public CSyncObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSemaphore::CSemaphore](#csemaphore)|构造 `CSemaphore` 对象。|

## <a name="remarks"></a>备注

信号量可用于控制对共享资源的访问, 而共享资源仅支持有限数量的用户。 `CSemaphore`对象的当前计数为允许的其他用户数。 当计数达到零时, 使用由`CSemaphore`对象控制的资源的所有尝试都将被插入到系统队列中并等待, 直到它们超时或计数上升到0以上。 在构造`CSemaphore`对象的过程中, 指定一次可以访问受控资源的最大用户数。

若要使用`CSemaphore`对象, 请在`CSemaphore`需要时构造对象。 指定想要等待的信号量的名称, 应用程序最初应拥有该信号量。 然后, 可以在构造函数返回时访问信号量。 完成访问受控资源后, 调用[CSyncObject:: Unlock](../../mfc/reference/csyncobject-class.md#unlock) 。

使用`CSemaphore`对象的一种替代方法是将类型`CSemaphore`的变量作为数据成员添加到要控制的类。 在构造受控对象的过程中, 调用`CSemaphore`数据成员的构造函数, 该构造函数指定初始访问计数、最大访问计数、信号量的名称 (如果将跨进程边界使用) 和所需的安全属性。

若要以这种`CSemaphore`方式访问由对象控制的资源, 请首先在资源的访问成员函数中创建类型为[CSingleLock](../../mfc/reference/csinglelock-class.md)或[CMultiLock](../../mfc/reference/cmultilock-class.md)的变量。 然后调用锁对象的`Lock`成员函数 (例如, [CSingleLock:: lock](../../mfc/reference/csinglelock-class.md#lock))。 此时, 你的线程将获取对资源的访问权限, 等待资源释放并获取访问权限, 或者等待资源释放并超时, 无法获取对资源的访问权限。 在任何情况下, 都已以线程安全的方式访问了资源。 若要释放资源, 请使用锁定对象的`Unlock`成员函数 (例如, [CSingleLock:: Unlock](../../mfc/reference/csinglelock-class.md#unlock)), 或允许锁定对象超出范围。

另外, 还可以创建一个`CSemaphore`独立的对象, 并在尝试访问受控资源之前显式访问该对象。 此方法虽然更清楚地了解你的源代码, 但更容易出错。

有关如何使用`CSemaphore`对象的详细信息, 请参阅[多线程处理:如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CSemaphore`

## <a name="requirements"></a>要求

**标头:** afxmt

##  <a name="csemaphore"></a>CSemaphore::CSemaphore

构造已命名或未`CSemaphore`命名的对象。

```
CSemaphore(
    LONG lInitialCount = 1,
    LONG lMaxCount = 1,
    LPCTSTR pstrName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```

### <a name="parameters"></a>参数

*lInitialCount*<br/>
信号量的初始使用计数。 必须大于或等于0且小于或等于*lMaxCount*。

*lMaxCount*<br/>
信号量的最大使用计数。 必须大于 0。

*pstrName*<br/>
信号量的名称。 如果将跨进程边界访问信号量, 则必须提供。 如果`NULL`为, 则对象将为未命名。 如果该名称与现有的信号量匹配, 则构造函数`CSemaphore`将生成一个新的对象, 该对象引用该名称的信号量。 如果该名称与非信号量的现有同步对象匹配, 则构造将失败。

*lpsaAttributes*<br/>
信号灯对象的安全特性。 有关此结构的完整说明, 请参阅 Windows SDK 中的[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 。

### <a name="remarks"></a>备注

若要访问或释放`CSemaphore`对象, 请创建[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)对象, 并调用其[锁定](../../mfc/reference/csinglelock-class.md#lock)和[取消锁定](../../mfc/reference/csinglelock-class.md#unlock)成员函数。

> [!IMPORTANT]
>  创建`CSemaphore`对象后, 使用[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)确保互斥体不存在。 如果互斥体确实存在, 则可能表示未强占恶意进程, 并可能会有意使用该互斥体。 在这种情况下, 建议的安全意识过程是关闭句柄, 然后继续操作, 就像创建对象时出错一样。

## <a name="see-also"></a>请参阅

[CSyncObject 类](../../mfc/reference/csyncobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
