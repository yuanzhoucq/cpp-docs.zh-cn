---
title: CMutex 类
ms.date: 11/04/2016
f1_keywords:
- CMutex
- AFXMT/CMutex
- AFXMT/CMutex::CMutex
helpviewer_keywords:
- CMutex [MFC], CMutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
ms.openlocfilehash: f85e562af9d048503be20d1ab5d219fe8d2d039f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62373625"
---
# <a name="cmutex-class"></a>CMutex 类

表示一个"互斥体"— 一个允许一个线程互斥独占访问资源的同步对象。

## <a name="syntax"></a>语法

```
class CMutex : public CSyncObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMutex::CMutex](#cmutex)|构造 `CMutex` 对象。|

## <a name="remarks"></a>备注

可以允许一次只有一个线程来修改数据或某个其他受控的资源时，互斥体很有用。 例如，将节点添加到链接的列表是一个过程，应仅允许一个线程通过一次。 通过使用`CMutex`对象以控制链接的列表中，仅一次一个线程可以访问列表。

若要使用`CMutex`对象，构造`CMutex`对象时需要它。 指定你想要等待，互斥体的名称和你的应用程序最初应拥有它。 构造函数返回时，您就可以访问互斥体。 调用[CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock)完成后访问受控的资源。

使用一种替代方法`CMutex`对象将添加一个类型的变量`CMutex`为想要控制此类数据成员。 在受控的对象的构造，过程调用的构造函数`CMutex`指定是否互斥体最初拥有，互斥体 （如果跨进程边界，将使用它），名称和所需的安全属性的数据成员。

由控制访问资源`CMutex`对象以这种方式，首先创建任一类型的变量[CSingleLock](../../mfc/reference/csinglelock-class.md)或类型[CMultiLock](../../mfc/reference/cmultilock-class.md)中资源的访问成员函数。 然后，调用的锁对象`Lock`成员函数 (例如， [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock))。 此时，你的线程将获取对资源的访问权限，等待资源释放并获取访问权限，或等待资源释放和超时，无法获取对资源的访问权限。 在任何情况下，以线程安全的方式访问所需的资源。 若要释放资源，使用的锁对象`Unlock`成员函数 (例如， [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock))，或允许离开作用域的锁对象。

有关使用的详细信息`CMutex`对象，请参阅文章[多线程处理：如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CMutex`

## <a name="requirements"></a>要求

**标头：** afxmt.h

##  <a name="cmutex"></a>  CMutex::CMutex

构造一个已命名或未命名的`CMutex`对象。

```
CMutex(
    BOOL bInitiallyOwn = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>参数

*bInitiallyOwn*<br/>
指定如果线程创建`CMutex`对象最初有权访问由 mutex 控制的资源。

*lpszName*<br/>
`CMutex` 对象的名称。 如果存在具有相同名称的另一个互斥体，则*lpszName*如果跨进程边界，将使用的对象必须提供。 如果**NULL**，将是未命名的互斥体。 如果名称匹配现有 mutex，构造函数将生成新`CMutex`对象引用该名称的互斥体。 如果名称匹配一个现有的同步对象，它不 mutex，构造将失败。

*lpsaAttribute*<br/>
Mutex 对象的安全特性。 此结构的完整说明，请参阅[SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) Windows SDK 中。

### <a name="remarks"></a>备注

访问或释放`CMutex`对象，请创建[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)对象，并调用其[锁](../../mfc/reference/csinglelock-class.md#lock)并[解锁](../../mfc/reference/csinglelock-class.md#unlock)成员函数。 如果`CMutex`正在独立使用对象，调用其`Unlock`成员函数以将其释放。

> [!IMPORTANT]
>  在创建后`CMutex`对象，请使用[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)以确保该互斥体已不存在。 如果该互斥体未意外存在，则可能表示一个恶意进程是占用并可能想要出于恶意使用互斥体。 在这种情况下，建议的注重安全的过程是关闭句柄并继续执行，如同创建对象时出错。

## <a name="see-also"></a>请参阅

[CSyncObject 类](../../mfc/reference/csyncobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
