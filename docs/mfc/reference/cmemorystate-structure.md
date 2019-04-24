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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62163749"
---
# <a name="cmemorystate-structure"></a>CMemoryState 结构

提供了方便地检测您的程序中的内存泄漏。

## <a name="syntax"></a>语法

```
struct CMemoryState
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMemoryState::CMemoryState](#cmemorystate)|构造一个类似于类的结构，用于控制内存检查点。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMemoryState::Checkpoint](#checkpoint)|获取当前内存状态的快照 （检查点）。|
|[CMemoryState::Difference](#difference)|计算两个对象的类型之间的差异`CMemoryState`。|
|[CMemoryState::DumpAllObjectsSince](#dumpallobjectssince)|转储自上一个检查点以来的所有当前分配的对象的摘要。|
|[CMemoryState::DumpStatistics](#dumpstatistics)|打印内存分配的统计信息`CMemoryState`对象。|

## <a name="remarks"></a>备注

`CMemoryState` 是一种结构，而未一个基类。

当对象内存是在堆上分配但未解除分配时不再需要时，将发生"内存泄漏"。 此类内存泄漏可能最终导致内存不足错误。 有几种方法来分配和释放在程序中的内存：

- 使用`malloc` /  `free`系列的函数的运行时库。

- 使用 Windows API 内存管理函数， `LocalAlloc` /  `LocalFree`并`GlobalAlloc` /  `GlobalFree`。

- 使用C++**新**并**删除**运算符。

`CMemoryState`诊断仅帮助检测内存泄漏时使用的内存分配导致**新**运算符会释放使用**删除**。 内存管理函数中的其他两个组都为非C++程序，并将它们与混合**新**并**删除**不建议在同一个程序。 提供附加的宏，DEBUG_NEW，替换**新**运算符时所需文件和行号跟踪内存分配。 每当你通常会使用时使用 DEBUG_NEW**新**运算符。

与其他诊断`CMemoryState`诊断程序仅在应用程序的调试版本中可用。 调试版本必须具有定义 _DEBUG 常量。

如果你怀疑你的程序可能具有的内存泄漏，可以使用`Checkpoint`， `Difference`，和`DumpStatistics`函数在程序执行过程中的两个不同点发现的内存状态 （分配的对象） 之间的差异。 此信息可以用于确定函数是否清理它再分配的所有对象。

如果只需知道在分配和解除分配不平衡出现的位置不会提供足够的信息，则可以使用`DumpAllObjectsSince`函数来转储自上一个调用分配的所有对象`Checkpoint`。 此转储显示了分配、 源文件和其中对象已分配 （如果使用的 DEBUG_NEW 分配），行的顺序和派生的对象，其地址和其大小。 `DumpAllObjectsSince` 此外会调用每个对象的`Dump`函数以提供有关其当前状态的信息。

有关如何使用详细信息`CMemoryState`和其他诊断，请参阅[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。

> [!NOTE]
>  类型的对象的声明`CMemoryState`和对成员函数的调用应括`#if defined(_DEBUG)/#endif`指令。 这会导致内存诊断功能以包含仅在调试程序的版本。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CMemoryState`

## <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="checkpoint"></a>  CMemoryState::Checkpoint

获取快照摘要的内存，并将其存储在此`CMemoryState`对象。

```
void Checkpoint();
```

### <a name="remarks"></a>备注

`CMemoryState`成员函数[差异](#difference)并[DumpAllObjectsSince](#dumpallobjectssince)使用此快照数据。

### <a name="example"></a>示例

  有关示例，请参阅[CMemoryState](#cmemorystate)构造函数。

##  <a name="cmemorystate"></a>  CMemoryState::CMemoryState

构造一个空`CMemoryState`对象，它必须通过填写[检查点](#checkpoint)或[差异](#difference)成员函数。

```
CMemoryState();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]

##  <a name="difference"></a>  Cmemorystate:: Difference

比较两个`CMemoryState`对象，然后将存储到此区别`CMemoryState`对象。

```
BOOL Difference(
    const CMemoryState& oldState,
    const CMemoryState& newState);
```

### <a name="parameters"></a>参数

*oldState*<br/>
由定义的初始内存状态`CMemoryState`检查点。

*newState*<br/>
按照定义的新内存状态`CMemoryState`检查点。

### <a name="return-value"></a>返回值

如果两个内存状态不同; 非零值否则为 0。

### <a name="remarks"></a>备注

[检查点](#checkpoint)必须为两个内存状态参数的每个调用。

### <a name="example"></a>示例

  有关示例，请参阅[CMemoryState](#cmemorystate)构造函数。

##  <a name="dumpallobjectssince"></a>  CMemoryState::DumpAllObjectsSince

调用`Dump`函数的所有对象类型的派生自类`CObject`的分配 （和仍分配） 自上次[检查点](#checkpoint)调用此`CMemoryState`对象。

```
void DumpAllObjectsSince() const;
```

### <a name="remarks"></a>备注

调用`DumpAllObjectsSince`使用未初始化`CMemoryState`对象将转储当前在内存中的所有对象。

### <a name="example"></a>示例

  有关示例，请参阅[CMemoryState](#cmemorystate)构造函数。

##  <a name="dumpstatistics"></a>  CMemoryState::DumpStatistics

将输出从简洁内存统计信息报告`CMemoryState`对象，它由填充[差异](#difference)成员函数。

```
void DumpStatistics() const;
```

### <a name="remarks"></a>备注

报表打印[afxDump](diagnostic-services.md#afxdump)设备，显示以下：

示例报表提供有关信息的数量 （或量）：

- 可用块

- 普通的块

- CRT 块

- 忽略基块

- 客户端块

- 在任何一个时间 （以字节为单位） 由程序所使用的最大内存

- 当前使用的程序 （以字节为单位） 的总内存

可用块是如果时延迟释放的块的数目`afxMemDF`已设置为`delayFreeMemDF`。 有关详细信息，请参阅[afxMemDF](diagnostic-services.md#afxmemdf)，在"MFC 宏和全局变量"部分。

### <a name="example"></a>示例

  下面的代码应置于*projname*app.cpp。 定义以下全局变量：

[!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]

在`InitInstance`函数中，添加行：

[!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]

添加的处理程序`ExitInstance`函数，并使用以下代码：

[!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]

现在可以运行该程序在调试模式下，若要查看的输出`DumpStatistics`函数。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)
