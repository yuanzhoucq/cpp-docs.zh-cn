---
title: CSemaphore 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSemaphore
- AFXMT/CSemaphore
- AFXMT/CSemaphore::CSemaphore
dev_langs:
- C++
helpviewer_keywords:
- CSemaphore [MFC], CSemaphore
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 19d43d108888d1d89b4fa6173ab3ebd0e8e55bbc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400245"
---
# <a name="csemaphore-class"></a>CSemaphore 类

类的对象`CSemaphore`表示一个"信号量"— 允许有限的数量的线程中一个或多个进程访问资源，并保持当前访问指定的资源的线程数的计数的同步对象。

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

信号量可控制到仅支持有限的数量的用户的共享资源的访问。 当前计数`CSemaphore`对象是其他允许的用户数。 所有计数达到零时，尝试使用由控制资源`CSemaphore`对象将插入到系统队列，并等待直到它们任一超时或计数大于 0。 构造期间指定的最大可以一次访问受控的资源的用户数`CSemaphore`对象。

若要使用`CSemaphore`对象，构造`CSemaphore`对象时需要它。 指定你想要等待信号量的名称和你的应用程序最初应拥有它。 构造函数返回时，您就可以访问信号量。 调用[CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock)完成后访问受控的资源。

使用一种替代方法`CSemaphore`对象将添加一个类型的变量`CSemaphore`为想要控制此类数据成员。 在受控的对象的构造，过程调用的构造函数`CSemaphore`指定初始数据成员访问计数、 最大访问次数、 信号量 （如果跨进程边界，将使用它） 的名称和所需的安全属性。

由控制访问资源`CSemaphore`对象以这种方式，首先创建任一类型的变量[CSingleLock](../../mfc/reference/csinglelock-class.md)或类型[CMultiLock](../../mfc/reference/cmultilock-class.md)中资源的访问成员函数。 然后，调用的锁对象`Lock`成员函数 (例如， [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock))。 此时，你的线程将获取对资源的访问权限，等待资源释放并获取访问权限，或等待资源释放和超时，无法获取对资源的访问权限。 在任何情况下，以线程安全的方式访问所需的资源。 若要释放资源，使用的锁对象`Unlock`成员函数 (例如， [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock))，或允许离开作用域的锁对象。

或者，可以创建`CSemaphore`对象独立的并尝试访问受控的资源之前显式访问。 此方法，同时更清晰的某个人可以读取源代码，很多容易出现错误。

有关如何使用的详细信息`CSemaphore`对象，请参阅文章[多线程处理： 如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CSemaphore`

## <a name="requirements"></a>要求

**标头：** afxmt.h

##  <a name="csemaphore"></a>  CSemaphore::CSemaphore

构造一个已命名或未命名的`CSemaphore`对象。

```
CSemaphore(
    LONG lInitialCount = 1,
    LONG lMaxCount = 1,
    LPCTSTR pstrName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```

### <a name="parameters"></a>参数

*lInitialCount*<br/>
初始的使用情况的信号量计数。 必须是大于或等于 0，且小于或等于*lMaxCount*。

*lMaxCount*<br/>
最大使用率的信号量计数。 必须大于 0。

*pstrName*<br/>
信号量的名称。 将跨进程边界访问信号量时，必须提供。 如果`NULL`，该对象将是未命名。 如果名称与现有的信号量相匹配，构造函数将生成新`CSemaphore`对象引用该名称的信号量。 如果名称与现有同步对象不是一个信号量相匹配，构造将失败。

*lpsaAttributes*<br/>
信号量对象的安全特性。 此结构的完整说明，请参阅[SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) Windows SDK 中。

### <a name="remarks"></a>备注

访问或释放`CSemaphore`对象，请创建[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)对象，并调用其[锁](../../mfc/reference/csinglelock-class.md#lock)并[解锁](../../mfc/reference/csinglelock-class.md#unlock)成员函数。

> [!IMPORTANT]
>  在创建后`CSemaphore`对象，请使用[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)以确保该互斥体已不存在。 如果该互斥体未意外存在，则可能表示一个恶意进程是占用并可能想要出于恶意使用互斥体。 在这种情况下，建议的注重安全的过程是关闭句柄并继续执行，如同创建对象时出错。

## <a name="see-also"></a>请参阅

[CSyncObject 类](../../mfc/reference/csyncobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)



