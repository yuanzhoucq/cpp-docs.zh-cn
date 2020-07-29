---
title: CMemoryState 结构
ms.date: 11/04/2016
f1_keywords:
- CMemoryState
helpviewer_keywords:
- CMemoryState structure [MFC]
- memory leaks [MFC], detecting
- detecting memory leaks [MFC]
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
ms.openlocfilehash: 823d424620e205d14f247a147bbf7dcb40a626b9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222909"
---
# <a name="cmemorystate-structure"></a>CMemoryState 结构

提供了一种方便的方法来检测程序中的内存泄漏。

## <a name="syntax"></a>语法

```
struct CMemoryState
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMemoryState：： CMemoryState](#cmemorystate)|构造控制内存检查点的类似于类的结构。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[CMemoryState：： Checkpoint](#checkpoint)|获取当前内存状态的快照（检查点）。|
|[CMemoryState：:D ifference](#difference)|计算类型的两个对象之间的差异 `CMemoryState` 。|
|[CMemoryState：:D umpAllObjectsSince](#dumpallobjectssince)|转储自上一个检查点以来所有当前分配的对象的摘要。|
|[CMemoryState：:D umpStatistics](#dumpstatistics)|打印对象的内存分配统计信息 `CMemoryState` 。|

## <a name="remarks"></a>备注

`CMemoryState`为结构，并且不具有基类。

当在堆上分配对象的内存，但在不再需要该对象时未释放该对象时，将发生 "内存泄漏"。 此类内存泄漏最终会导致内存不足错误。 可以通过多种方式在程序中分配和释放内存：

- 使用 `malloc` /  `free` 运行时库中的函数系列。

- 使用 Windows API 内存管理函数 `LocalAlloc` /  `LocalFree` 和 `GlobalAlloc` /  `GlobalFree` 。

- 使用 c + + **`new`** 和 **`delete`** 运算符。

`CMemoryState`仅当 **`new`** 未使用释放使用运算符分配的内存时，诊断程序帮助检测内存泄漏 **`delete`** 。 其他两组内存管理函数适用于非 C + + 程序，并且 **`new`** **`delete`** 不建议在同一程序中将它们与和混合使用。 提供了一个 DEBUG_NEW 的附加宏，用于 **`new`** 在需要内存分配的文件和行号跟踪时替换运算符。 当你通常使用运算符时，将使用 DEBUG_NEW **`new`** 。

与其他诊断一样， `CMemoryState` 诊断仅在程序的调试版本中可用。 调试版本必须定义 _DEBUG 常数。

如果你怀疑你的程序有内存泄漏，则可以使用 `Checkpoint` 、 `Difference` 和 `DumpStatistics` 函数来发现程序执行中两个不同点上的内存状态（分配的对象）之间的差异。 此信息可用于确定某个函数是否正在清理它分配的所有对象。

如果只是了解分配和解除分配不平衡的位置不能提供足够的信息，则可以使用 `DumpAllObjectsSince` 函数转储自上一次调用后分配的所有对象 `Checkpoint` 。 此转储显示分配的顺序、存储对象的源文件和行（如果使用的是 DEBUG_NEW 进行分配）以及对象的派生、其地址和大小。 `DumpAllObjectsSince`还会调用每个对象的 `Dump` 函数，以提供有关其当前状态的信息。

有关如何使用 `CMemoryState` 和其他诊断的详细信息，请参阅[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。

> [!NOTE]
> 类型的对象的声明 `CMemoryState` 和成员函数的调用都应该用指令括起来 `#if defined(_DEBUG)/#endif` 。 这将导致内存诊断仅包含在调试程序的版本中。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CMemoryState`

## <a name="requirements"></a>要求

**标头：** afx

## <a name="cmemorystatecheckpoint"></a><a name="checkpoint"></a>CMemoryState：： Checkpoint

拍摄内存快照摘要，并将其存储在此 `CMemoryState` 对象中。

```cpp
void Checkpoint();
```

### <a name="remarks"></a>备注

`CMemoryState`成员函数[差别](#difference)和[DumpAllObjectsSince](#dumpallobjectssince)使用此快照数据。

### <a name="example"></a>示例

  请参阅[CMemoryState](#cmemorystate)构造函数的示例。

## <a name="cmemorystatecmemorystate"></a><a name="cmemorystate"></a>CMemoryState：： CMemoryState

构造一个 `CMemoryState` 必须由[检查点](#checkpoint)或[差异](#difference)成员函数填充的空对象。

```
CMemoryState();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]

## <a name="cmemorystatedifference"></a><a name="difference"></a>CMemoryState：:D ifference

比较两个 `CMemoryState` 对象，然后将其存储在此 `CMemoryState` 对象中。

```
BOOL Difference(
    const CMemoryState& oldState,
    const CMemoryState& newState);
```

### <a name="parameters"></a>参数

*oldState*<br/>
检查点定义的初始内存状态 `CMemoryState` 。

*newState*<br/>
检查点定义的新内存状态 `CMemoryState` 。

### <a name="return-value"></a>返回值

如果两个内存状态不同，则为非零值;否则为0。

### <a name="remarks"></a>备注

必须已为每个内存状态参数调用了[检查点](#checkpoint)。

### <a name="example"></a>示例

  请参阅[CMemoryState](#cmemorystate)构造函数的示例。

## <a name="cmemorystatedumpallobjectssince"></a><a name="dumpallobjectssince"></a>CMemoryState：:D umpAllObjectsSince

对 `Dump` 从类派生的类型的所有对象调用函数，该类型是从 `CObject` 该对象的最后一个[检查点](#checkpoint)调用以来已分配（并且仍被分配）的 `CMemoryState` 。

```cpp
void DumpAllObjectsSince() const;
```

### <a name="remarks"></a>备注

`DumpAllObjectsSince`使用未初始化的 `CMemoryState` 对象调用会转储当前在内存中的所有对象。

### <a name="example"></a>示例

  请参阅[CMemoryState](#cmemorystate)构造函数的示例。

## <a name="cmemorystatedumpstatistics"></a><a name="dumpstatistics"></a>CMemoryState：:D umpStatistics

从 `CMemoryState` 由[差异](#difference)成员函数填充的对象打印简洁的内存统计信息报表。

```cpp
void DumpStatistics() const;
```

### <a name="remarks"></a>备注

在[afxDump](diagnostic-services.md#afxdump)设备上打印的报表显示以下内容：

示例报表提供有关的数量（或数量）的信息：

- 可用块

- 正常块

- CRT 块

- 忽略块

- 客户端块

- 程序在任何一次使用的最大内存（以字节为单位）

- 当前程序使用的内存总量（以字节为单位）

可用块是设置为时延迟释放的块的数量 `afxMemDF` `delayFreeMemDF` 。 有关详细信息，请参阅 "MFC 宏和全局" 部分的[afxMemDF](diagnostic-services.md#afxmemdf)。

### <a name="example"></a>示例

  应将以下代码放置在*projname*的应用程序中。 定义以下全局变量：

[!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]

在 `InitInstance` 函数中，添加行：

[!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]

为函数添加处理程序 `ExitInstance` 并使用以下代码：

[!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]

你现在可以在调试模式下运行程序，以查看函数的输出 `DumpStatistics` 。

## <a name="see-also"></a>另请参阅

[层次结构图](../../mfc/hierarchy-chart.md)
