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
ms.openlocfilehash: 2d6f637ab4828b3e70df205ebf359ae45a940d60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363282"
---
# <a name="cmutex-class"></a>CMutex 类

表示"互斥"-允许一个线程相互独占的资源的同步对象。

## <a name="syntax"></a>语法

```
class CMutex : public CSyncObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMutex：CMutex](#cmutex)|构造 `CMutex` 对象。|

## <a name="remarks"></a>备注

当一次只允许一个线程修改数据或其他受控资源时，Mutexs 非常有用。 例如，将节点添加到链接列表是一个一次只能由一个线程允许的过程。 通过使用`CMutex`对象来控制链接列表，一次只能访问一个线程。

要使用`CMutex`对象，`CMutex`在需要对象时构造该对象。 指定要等待的互斥体的名称，并且应用程序最初应拥有它。 然后，当构造函数返回时，可以访问互斥体。 调用[CSyncObject：：访问](../../mfc/reference/csyncobject-class.md#unlock)受控资源后解锁。

使用`CMutex`对象的替代方法是将类型的`CMutex`变量作为数据成员添加到要控制的类中。 在构造受控对象期间，调用`CMutex`数据成员的构造函数，指定互斥体最初是否拥有、互斥体的名称（如果它将跨进程边界使用）以及所需的安全属性。

要以这种方式访问受`CMutex`对象控制的资源，请首先在资源的访问成员函数中创建[CSingleLock](../../mfc/reference/csinglelock-class.md)类型或[CMultiLock](../../mfc/reference/cmultilock-class.md)类型的变量。 然后调用锁对象`Lock`的成员函数（例如[，CSingleLock：：锁定](../../mfc/reference/csinglelock-class.md#lock)）。 此时，线程将获取对资源的访问，等待资源被释放并获取访问权限，或者等待资源释放和超时，无法访问资源。 在任何情况下，您的资源都以线程安全的方式访问。 要释放资源，请使用锁定对象`Unlock`的成员函数（例如[，CSingleLock：：解锁](../../mfc/reference/csinglelock-class.md#unlock)），或允许锁定对象退出范围。

有关使用`CMutex`对象的详细信息，请参阅"[多线程：如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)"一文。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CMutex`

## <a name="requirements"></a>要求

**标题：** afxmt.h

## <a name="cmutexcmutex"></a><a name="cmutex"></a>CMutex：CMutex

构造命名或未命名`CMutex`的对象。

```
CMutex(
    BOOL bInitiallyOwn = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>参数

*b 初始拥有*<br/>
指定创建`CMutex`对象的线程最初是否有权访问由互斥体控制的资源。

*lpsz名称*<br/>
`CMutex` 对象的名称。 如果存在另一个同名的互斥体，则必须提供*lpszName，* 如果对象将跨进程边界使用。 如果**NULL**，则互斥体将未命名。 如果名称与现有互斥体匹配，则构造函数将生成一`CMutex`个新对象，该对象引用该名称的互斥体。 如果名称与现有不是互斥体的同步对象匹配，则构造将失败。

*lpsa属性*<br/>
互斥体的安全属性。 有关此结构的完整说明，请参阅 Windows SDK 中的[SECURITY_ATTRIBUTES。](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))

### <a name="remarks"></a>备注

要访问或`CMutex`释放对象，请创建[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)对象，并调用其[锁定](../../mfc/reference/csinglelock-class.md#lock)和[解锁](../../mfc/reference/csinglelock-class.md#unlock)成员函数。 如果对象`CMutex`是独立使用的，请调用其成员`Unlock`函数以释放它。

> [!IMPORTANT]
> 创建对象后`CMutex`，请使用[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)确保互斥体不存在。 如果互斥体确实意外存在，则可能表示恶意进程正在蹲下，并且可能打算恶意使用互斥体。 在这种情况下，建议的安全意识过程是关闭句柄并继续，就像创建对象时失败一样。

## <a name="see-also"></a>另请参阅

[CSync对象类](../../mfc/reference/csyncobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
