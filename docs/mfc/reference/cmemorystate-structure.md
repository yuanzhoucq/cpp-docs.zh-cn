---
title: 内存状态结构
ms.date: 11/04/2016
f1_keywords:
- CMemoryState
helpviewer_keywords:
- CMemoryState structure [MFC]
- memory leaks [MFC], detecting
- detecting memory leaks [MFC]
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
ms.openlocfilehash: 94a2fb65a9a3030f9dc683d0eb30f476b9de1cad
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752610"
---
# <a name="cmemorystate-structure"></a>内存状态结构

提供了一种检测程序中内存泄漏的便捷方法。

## <a name="syntax"></a>语法

```
struct CMemoryState
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C内存状态：：CMemoryState](#cmemorystate)|构造控制内存检查点的类结构。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMemoryState：检查点](#checkpoint)|获取当前内存状态的快照（检查点）。|
|[CMemoryState：:D](#difference)|计算类型`CMemoryState`两个对象之间的差异。|
|[CMemoryState：:D个ump所有对象](#dumpallobjectssince)|转储自上次检查点以来当前分配的所有对象的摘要。|
|[CMemoryState：:Dump统计](#dumpstatistics)|打印`CMemoryState`对象的内存分配统计信息。|

## <a name="remarks"></a>备注

`CMemoryState`是一个结构，没有基类。

当在堆上分配对象的内存，但在不再需要对象时未进行处理时，就会发生"内存泄漏"。 此类内存泄漏最终可能导致内存不足错误。 在程序中分配和分配内存的方法有多种：

- 使用运行时库中的函数`free`系列。 `malloc` / 

- 使用 Windows API 内存管理`LocalAlloc`/ `LocalFree`功能`GlobalAlloc`/ `GlobalFree`和 。

- 使用C++**新的**运算符和**删除**运算符。

诊断`CMemoryState`仅有助于检测使用**新**运算符分配的内存未使用**delete**进行定位时导致的内存泄漏。 另外两组内存管理功能用于非C++程序，不建议将它们与同一程序中**的新**程序和**删除**程序混合。 提供了一个额外的宏，DEBUG_NEW，用于在需要内存分配的文件和行号跟踪时替换**新**运算符。 每当您通常使用**新**运算符时，都会使用DEBUG_NEW。

与其他诊断一样，`CMemoryState`诊断仅在程序的调试版本中可用。 调试版本必须定义_DEBUG常量。

如果您怀疑程序存在内存泄漏，则可以使用`Checkpoint`和`Difference``DumpStatistics`函数来发现在程序执行中的两个不同点内存状态（分配的对象）之间的差异。 此信息可用于确定函数是否正在清理它分配的所有对象。

如果仅仅知道分配和分配位置的不平衡位置没有提供足够的信息，则可以使用 函数`DumpAllObjectsSince`转储自上次调用`Checkpoint`以来分配的所有对象。 此转储显示分配顺序、分配对象的源文件和行（如果使用DEBUG_NEW进行分配），以及对象、地址和大小的派生。 `DumpAllObjectsSince`还会调用每个对象的`Dump`函数来提供有关其当前状态的信息。

有关如何使用`CMemoryState`和其他诊断的详细信息，请参阅[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。

> [!NOTE]
> 类型`CMemoryState`对象声明和对成员函数的调用应用`#if defined(_DEBUG)/#endif`指令括括号。 这将导致内存诊断仅包含在程序的调试生成中。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CMemoryState`

## <a name="requirements"></a>要求

**标题：** afx.h

## <a name="cmemorystatecheckpoint"></a><a name="checkpoint"></a>CMemoryState：检查点

获取内存的快照摘要并将其存储在此`CMemoryState`对象中。

```cpp
void Checkpoint();
```

### <a name="remarks"></a>备注

成员`CMemoryState`函数["差异](#difference)"和["转储所有对象"自](#dumpallobjectssince)使用此快照数据。

### <a name="example"></a>示例

  请参阅[CMemoryState](#cmemorystate)构造函数的示例。

## <a name="cmemorystatecmemorystate"></a><a name="cmemorystate"></a>C内存状态：：CMemoryState

构造必须由`CMemoryState`[检查点](#checkpoint)或[差异](#difference)成员函数填充的空对象。

```
CMemoryState();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]

## <a name="cmemorystatedifference"></a><a name="difference"></a>CMemoryState：:D

比较两`CMemoryState`个对象，然后将差异存储到此`CMemoryState`对象中。

```
BOOL Difference(
    const CMemoryState& oldState,
    const CMemoryState& newState);
```

### <a name="parameters"></a>参数

*旧州*<br/>
由`CMemoryState`检查点定义的初始内存状态。

*newState*<br/>
由`CMemoryState`检查点定义的新内存状态。

### <a name="return-value"></a>返回值

如果两个内存状态不同，则非零;否则 0。

### <a name="remarks"></a>备注

必须为两个内存状态参数中的每一个调用[检查点](#checkpoint)。

### <a name="example"></a>示例

  请参阅[CMemoryState](#cmemorystate)构造函数的示例。

## <a name="cmemorystatedumpallobjectssince"></a><a name="dumpallobjectssince"></a>CMemoryState：:D个ump所有对象

调用自`Dump`上次[检查点](#checkpoint)调用此`CMemoryState`对象以来从类`CObject`派生（并且仍已分配）的类型的所有对象的函数。

```cpp
void DumpAllObjectsSince() const;
```

### <a name="remarks"></a>备注

使用`DumpAllObjectsSince`未初始化`CMemoryState`的对象调用将转储当前内存中的所有对象。

### <a name="example"></a>示例

  请参阅[CMemoryState](#cmemorystate)构造函数的示例。

## <a name="cmemorystatedumpstatistics"></a><a name="dumpstatistics"></a>CMemoryState：:Dump统计

从由`CMemoryState`[差异](#difference)成员函数填充的对象打印简明的内存统计信息报表。

```cpp
void DumpStatistics() const;
```

### <a name="remarks"></a>备注

打印在[afxDump](diagnostic-services.md#afxdump)设备上的报表显示以下内容：

示例报告提供有关以下数字（或数量）的信息：

- 自由方块

- 正常块

- CRT 块

- 忽略块

- 客户端块

- 程序在任何一次使用的最大内存（以字节为单位）

- 程序当前使用的总内存（以字节为单位）

自由块是如果设置为`afxMemDF``delayFreeMemDF`延迟的块数。 有关详细信息，请参阅"MFC 宏和全局"部分中的[afxMemDF。](diagnostic-services.md#afxmemdf)

### <a name="example"></a>示例

  以下代码应放在*projname*App.cpp 中。 定义以下全局变量：

[!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]

在`InitInstance`函数中，添加行：

[!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]

为`ExitInstance`函数添加处理程序并使用以下代码：

[!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]

您现在可以在调试模式下运行该程序以查看`DumpStatistics`函数的输出。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)
