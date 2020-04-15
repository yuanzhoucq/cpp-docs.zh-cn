---
title: C临界节类
ms.date: 11/04/2016
f1_keywords:
- CCriticalSection
- AFXMT/CCriticalSection
- AFXMT/CCriticalSection::CCriticalSection
- AFXMT/CCriticalSection::Lock
- AFXMT/CCriticalSection::Unlock
- AFXMT/CCriticalSection::m_sect
helpviewer_keywords:
- CCriticalSection [MFC], CCriticalSection
- CCriticalSection [MFC], Lock
- CCriticalSection [MFC], Unlock
- CCriticalSection [MFC], m_sect
ms.assetid: f776f74b-5b0b-4f32-9c13-2b8e4a0d7b2b
ms.openlocfilehash: d79199a332f6930619e6b4995b04bc590b6ea580
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369367"
---
# <a name="ccriticalsection-class"></a>C临界节类

表示"关键部分" - 一个同步对象，允许一次一个线程访问资源或代码部分。

## <a name="syntax"></a>语法

```
class CCriticalSection : public CSyncObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C关键部分：C关键节](#ccriticalsection)|构造 `CCriticalSection` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C关键部分：锁定](#lock)|用于访问`CCriticalSection`对象。|
|[C关键部分：解锁](#unlock)|释放 `CCriticalSection` 对象。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[C关键部分：：操作员CRITICAL_SECTION*](#operator_critical_section_star)|检索指向内部CRITICAL_SECTION对象的指针。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[C关键节：：m_sect](#m_sect)|对象CRITICAL_SECTION。|

## <a name="remarks"></a>备注

当一次只允许一个线程修改数据或其他受控资源时，关键部分非常有用。 例如，将节点添加到链接列表是一个一次只能由一个线程允许的过程。 通过使用`CCriticalSection`对象来控制链接列表，一次只能访问一个线程。

> [!NOTE]
> `CCriticalSection`类的功能由实际的 Win32 CRITICAL_SECTION对象提供。

当速度至关重要且资源不会跨进程边界使用时，将使用关键部分代替互斥（请参阅[CMutex）。](../../mfc/reference/cmutex-class.md)

使用`CCriticalSection`对象有两种方法：独立和嵌入类。

- 独立方法 使用独立`CCriticalSection`对象，在需要时构造`CCriticalSection`该对象。 从构造函数成功返回后，显式锁定对象，调用[Lock](#lock)。 访问关键部分后，调用[解锁](#unlock)。 此方法虽然对读取源代码的人更清晰，但更容易出错，因为您必须记住在访问前后锁定和解锁关键部分。

   更可取的方法是使用[CSingleLock](../../mfc/reference/csinglelock-class.md)类。 它还具有 和`Lock``Unlock`方法，但如果发生异常，您不必担心解锁资源。

- 嵌入式方法 您还可以通过向类中添加`CCriticalSection`-type 数据成员并在需要时锁定数据成员，与多个线程共享类。

有关使用`CCriticalSection`对象的详细信息，请参阅"[多线程：如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)"一文。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CCriticalSection`

## <a name="requirements"></a>要求

**标题：** afxmt.h

## <a name="ccriticalsectionccriticalsection"></a><a name="ccriticalsection"></a>C关键部分：C关键节

构造 `CCriticalSection` 对象。

```
CCriticalSection();
```

### <a name="remarks"></a>备注

要访问`CCriticalSection`或释放对象，请创建一个[CSingleLock](../../mfc/reference/csinglelock-class.md)对象，并调用其[锁定](../../mfc/reference/csinglelock-class.md#lock)和[解锁](../../mfc/reference/csinglelock-class.md#unlock)成员函数。 如果对象`CCriticalSection`是独立使用的，请调用其[Unlock](#unlock)成员函数以释放它。

如果构造函数无法分配所需的系统内存，将自动引发内存异常[（CMemoryException](../../mfc/reference/cmemoryexception-class.md)类型）。

### <a name="example"></a>示例

  请参阅[C关键节的示例：：锁定](#lock)。

## <a name="ccriticalsectionlock"></a><a name="lock"></a>C关键部分：锁定

调用此成员函数以访问关键部分对象。

```
BOOL Lock();
BOOL Lock(DWORD dwTimeout);
```

### <a name="parameters"></a>参数

*dwTimeout*<br/>
`Lock`忽略此参数值。

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0。

### <a name="remarks"></a>备注

`Lock`是阻塞调用，在关键截面对象发出信号（变为可用）之前不会返回。

如果需要时等待时间，可以使用[CMutex](../../mfc/reference/cmutex-class.md)对象而不是`CCriticalSection`对象。

如果`Lock`无法分配必要的系统内存，将自动引发内存异常[（CMemoryException](../../mfc/reference/cmemoryexception-class.md)类型）。

### <a name="example"></a>示例

此示例演示嵌套关键部分方法，方法是使用共享`_strShared``CCriticalSection`对象控制对共享资源（静态对象）的访问。 该`SomeMethod`函数演示以安全的方式更新共享资源。

[!code-cpp[NVC_MFC_Utilities#11](../../mfc/codesnippet/cpp/ccriticalsection-class_1.h)]

## <a name="ccriticalsectionm_sect"></a><a name="m_sect"></a>C关键节：：m_sect

包含所有`CCriticalSection`方法使用的关键节对象。

```
CRITICAL_SECTION m_sect;
```

## <a name="ccriticalsectionoperator-critical_section"></a><a name="operator_critical_section_star"></a>C关键部分：：操作员CRITICAL_SECTION*

检索CRITICAL_SECTION对象。

```
operator CRITICAL_SECTION*();
```

### <a name="remarks"></a>备注

调用此函数以检索指向内部CRITICAL_SECTION对象的指针。

## <a name="ccriticalsectionunlock"></a><a name="unlock"></a>C关键部分：解锁

释放`CCriticalSection`对象以供另一个线程使用。

```
BOOL Unlock();
```

### <a name="return-value"></a>返回值

如果`CCriticalSection`对象为线程所有且释放成功，则非零;否则 0。

### <a name="remarks"></a>备注

如果正在`CCriticalSection`独立使用 ，`Unlock`则必须在完成关键部分控制的资源的使用后立即调用。 如果使用[CSingleLock](../../mfc/reference/csinglelock-class.md)对象，`CCriticalSection::Unlock`则锁定对象`Unlock`的成员函数将调用该对象。

### <a name="example"></a>示例

  请参阅[C关键节的示例：：锁定](#lock)。

## <a name="see-also"></a>另请参阅

[CSync对象类](../../mfc/reference/csyncobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CMutex 类](../../mfc/reference/cmutex-class.md)
