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
ms.openlocfilehash: a110e1345cb970c117de125bd8105e1bc86eaf94
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855250"
---
# <a name="cmemorystate-structure"></a>CMemoryState 结构

提供了一种方便的方法来检测程序中的内存泄漏。

## <a name="syntax"></a>语法

```
struct CMemoryState
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMemoryState：： CMemoryState](#cmemorystate)|构造控制内存检查点的类似于类的结构。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMemoryState：： Checkpoint](#checkpoint)|获取当前内存状态的快照（检查点）。|
|[CMemoryState：:D ifference](#difference)|计算 `CMemoryState`类型的两个对象之间的差异。|
|[CMemoryState：:D umpAllObjectsSince](#dumpallobjectssince)|转储自上一个检查点以来所有当前分配的对象的摘要。|
|[CMemoryState：:D umpStatistics](#dumpstatistics)|打印 `CMemoryState` 对象的内存分配统计信息。|

## <a name="remarks"></a>备注

`CMemoryState` 是一种结构，没有基类。

当在堆上分配对象的内存，但在不再需要该对象时未释放该对象时，将发生 "内存泄漏"。 此类内存泄漏最终会导致内存不足错误。 可以通过多种方式在程序中分配和释放内存：

- 使用 `malloc`/ 运行时库中的 `free` 系列函数。

- 使用 Windows API 内存管理功能，`LocalAlloc`/ `LocalFree` 并 `GlobalAlloc`/ `GlobalFree`。

- C++使用**new**和**delete**运算符。

仅当使用**new**运算符分配的内存未使用**delete**取消分配时，`CMemoryState` 诊断才能帮助检测内存泄漏。 其他两组内存管理函数适用于非C++程序，不建议在同一程序中将它们与**new**和**delete**混合使用。 如果需要对内存分配进行文件和行号跟踪，则将提供一个附加的宏 DEBUG_NEW 来替换**NEW**运算符。 使用**NEW**运算符时，将使用 DEBUG_NEW。

与其他诊断一样，`CMemoryState` 诊断仅在程序的调试版本中可用。 调试版本必须定义 _DEBUG 常数。

如果你怀疑你的程序有内存泄漏，则可以使用 `Checkpoint`、`Difference`和 `DumpStatistics` 函数来发现程序执行中两个不同点上的内存状态（分配的对象）之间的差异。 此信息可用于确定某个函数是否正在清理它分配的所有对象。

如果只是了解分配和解除分配不平衡的位置不能提供足够的信息，则可以使用 `DumpAllObjectsSince` 函数转储自上一次调用 `Checkpoint`以来分配的所有对象。 此转储显示分配的顺序、存储对象的源文件和行（如果使用的是 DEBUG_NEW 进行分配）以及对象的派生、其地址和大小。 `DumpAllObjectsSince` 还会调用每个对象的 `Dump` 函数以提供有关其当前状态的信息。

有关如何使用 `CMemoryState` 和其他诊断的详细信息，请参阅[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。

> [!NOTE]
>  `CMemoryState` 类型的对象的声明和成员函数的调用都应由 `#if defined(_DEBUG)/#endif` 指令括起来。 这将导致内存诊断仅包含在调试程序的版本中。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CMemoryState`

## <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="checkpoint"></a>CMemoryState：： Checkpoint

拍摄内存快照摘要，并将其存储在此 `CMemoryState` 对象中。

```
void Checkpoint();
```

### <a name="remarks"></a>备注

`CMemoryState` 成员函数[差别](#difference)和[DumpAllObjectsSince](#dumpallobjectssince)使用此快照数据。

### <a name="example"></a>示例

  请参阅[CMemoryState](#cmemorystate)构造函数的示例。

##  <a name="cmemorystate"></a>CMemoryState：： CMemoryState

构造一个空的 `CMemoryState` 对象，该对象必须由[检查点](#checkpoint)或[差异](#difference)成员函数填充。

```
CMemoryState();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]

##  <a name="difference"></a>CMemoryState：:D ifference

比较两个 `CMemoryState` 对象，然后将这两个对象存储到此 `CMemoryState` 对象中。

```
BOOL Difference(
    const CMemoryState& oldState,
    const CMemoryState& newState);
```

### <a name="parameters"></a>参数

*oldState*<br/>
`CMemoryState` 检查点定义的初始内存状态。

*newState*<br/>
`CMemoryState` 检查点定义的新内存状态。

### <a name="return-value"></a>返回值

如果两个内存状态不同，则为非零值;否则为0。

### <a name="remarks"></a>备注

必须已为每个内存状态参数调用了[检查点](#checkpoint)。

### <a name="example"></a>示例

  请参阅[CMemoryState](#cmemorystate)构造函数的示例。

##  <a name="dumpallobjectssince"></a>CMemoryState：:D umpAllObjectsSince

对从类 `CObject` 派生的类型的所有对象调用 `Dump` 函数，该类型是从对此 `CMemoryState` 对象的最后一个[检查点](#checkpoint)调用以来已分配（并且仍被分配）的。

```
void DumpAllObjectsSince() const;
```

### <a name="remarks"></a>备注

使用未初始化的 `CMemoryState` 对象调用 `DumpAllObjectsSince` 会转储当前在内存中的所有对象。

### <a name="example"></a>示例

  请参阅[CMemoryState](#cmemorystate)构造函数的示例。

##  <a name="dumpstatistics"></a>CMemoryState：:D umpStatistics

从由[差异](#difference)成员函数填充的 `CMemoryState` 对象打印简洁的内存统计信息报表。

```
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

"可用块" 是 `afxMemDF` 设置为 `delayFreeMemDF`时延迟释放的块的数量。 有关详细信息，请参阅 "MFC 宏和全局" 部分的[afxMemDF](diagnostic-services.md#afxmemdf)。

### <a name="example"></a>示例

  应将以下代码放置在*projname*的应用程序中。 定义以下全局变量：

[!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]

在 `InitInstance` 函数中，添加以下行：

[!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]

为 `ExitInstance` 函数添加处理程序，然后使用以下代码：

[!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]

你现在可以在调试模式下运行程序，以查看 `DumpStatistics` 函数的输出。

## <a name="see-also"></a>另请参阅

[层次结构图](../../mfc/hierarchy-chart.md)
