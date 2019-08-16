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
ms.openlocfilehash: 65f7f4db9489de1c9a380d760ed5cab41bfdc2ec
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504517"
---
# <a name="cmutex-class"></a>CMutex 类

表示一个 "互斥体"-一种同步对象, 允许一个线程互相排斥地访问资源。

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

如果一次只能有一个线程可以修改数据或某些其他受控资源, 互斥体非常有用。 例如, 将节点添加到链接列表是一次只允许一个线程的进程。 通过使用`CMutex`对象控制链接列表, 一次只能有一个线程可以访问该列表。

若要使用`CMutex`对象, 请在`CMutex`需要时构造对象。 指定要等待的 mutex 的名称, 应用程序最初应拥有该名称。 然后, 你可以在构造函数返回时访问 mutex。 完成访问受控资源后, 调用[CSyncObject:: Unlock](../../mfc/reference/csyncobject-class.md#unlock) 。

使用`CMutex`对象的一种替代方法是将类型`CMutex`的变量作为数据成员添加到要控制的类。 在构造受控对象的过程中, 调用`CMutex`数据成员的构造函数, 该构造函数指定互斥体最初是否拥有, 互斥体的名称 (如果将跨进程边界使用) 和所需的安全特性。

若要以这种`CMutex`方式访问由对象控制的资源, 请首先在资源的访问成员函数中创建类型为[CSingleLock](../../mfc/reference/csinglelock-class.md)或[CMultiLock](../../mfc/reference/cmultilock-class.md)的变量。 然后调用锁对象的`Lock`成员函数 (例如, [CSingleLock:: lock](../../mfc/reference/csinglelock-class.md#lock))。 此时, 你的线程将获取对资源的访问权限, 等待资源释放并获取访问权限, 或者等待资源释放并超时, 无法获取对资源的访问权限。 在任何情况下, 都已以线程安全的方式访问了资源。 若要释放资源, 请使用锁定对象的`Unlock`成员函数 (例如, [CSingleLock:: Unlock](../../mfc/reference/csinglelock-class.md#unlock)), 或允许锁定对象超出范围。

有关使用`CMutex`对象的详细信息, 请参阅[多线程处理:如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CMutex`

## <a name="requirements"></a>要求

**标头:** afxmt

##  <a name="cmutex"></a>CMutex::CMutex

构造已命名或未`CMutex`命名的对象。

```
CMutex(
    BOOL bInitiallyOwn = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>参数

*bInitiallyOwn*<br/>
指定创建`CMutex`对象的线程最初是否可以访问由 mutex 控制的资源。

*lpszName*<br/>
`CMutex` 对象的名称。 如果存在另一个具有相同名称的 mutex, 则必须提供*lpszName* , 前提是该对象将跨进程边界使用。 如果**为 NULL**, 则 mutex 将为未命名。 如果该名称与现有互斥体匹配, 则构造函数将`CMutex`生成一个引用该名称互斥体的新对象。 如果该名称与不是 mutex 的现有同步对象匹配, 则构造将失败。

*lpsaAttribute*<br/>
Mutex 对象的安全特性。 有关此结构的完整说明, 请参阅 Windows SDK 中的[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 。

### <a name="remarks"></a>备注

若要访问或释放`CMutex`对象, 请创建[CMultiLock](../../mfc/reference/cmultilock-class.md)或[CSingleLock](../../mfc/reference/csinglelock-class.md)对象, 并调用其[锁定](../../mfc/reference/csinglelock-class.md#lock)和[取消锁定](../../mfc/reference/csinglelock-class.md#unlock)成员函数。 如果该`CMutex`对象是独立使用的, 请调用其`Unlock`成员函数将其释放。

> [!IMPORTANT]
>  创建`CMutex`对象后, 使用[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)确保互斥体不存在。 如果互斥体确实存在, 则可能表示未强占恶意进程, 并可能会有意使用该互斥体。 在这种情况下, 建议的安全意识过程是关闭句柄, 然后继续操作, 就像创建对象时出错一样。

## <a name="see-also"></a>请参阅

[CSyncObject 类](../../mfc/reference/csyncobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
