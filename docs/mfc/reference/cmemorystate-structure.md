---
title: CMemoryState 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMemoryState
dev_langs:
- C++
helpviewer_keywords:
- CMemoryState structure [MFC]
- memory leaks [MFC], detecting
- detecting memory leaks [MFC]
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d9dbcaa3f8e02a87713363f1ea38c5d2260171df
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cmemorystate-structure"></a>CMemoryState 结构
提供一种简便方式检测你的程序中的内存泄漏。  
  
## <a name="syntax"></a>语法  
  
```  
struct CMemoryState  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMemoryState::CMemoryState](#cmemorystate)|构造控制内存检查点以类似于类的结构。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMemoryState::Checkpoint](#checkpoint)|获取当前的内存状态的快照 （检查点）。|  
|[CMemoryState::Difference](#difference)|计算类型的两个对象之间的差`CMemoryState`。|  
|[Cmemorystate:: Dumpallobjectssince](#dumpallobjectssince)|自上一个检查点以来转储所有当前分配的对象的摘要。|  
|[CMemoryState::DumpStatistics](#dumpstatistics)|打印内存分配的统计信息`CMemoryState`对象。|  
  
## <a name="remarks"></a>备注  
 `CMemoryState` 是一种结构，并且没有基类。  
  
 对象的内存是堆中分配但未释放不再需要时，会出现"内存泄漏"。 此类内存泄漏可能最终导致内存不足错误。 有多种方式来分配和释放在程序中的内存：  
  
-   使用`malloc` / **免费**系列的函数的运行时库。  
  
-   使用 Windows API 内存管理函数， **LocalAlloc**/ **LocalFree**和**GlobalAlloc**/ **GlobalFree**.  
  
-   使用 c + +**新**和**删除**运算符。  
  
 `CMemoryState`诊断仅帮助检测内存泄漏时使用的内存分配导致**新**运算符会释放使用**删除**。 内存管理函数中的其他两个组适用于非 c + + 程序，并将它们与混合**新**和**删除**不建议在同一个程序。 其他的宏， `DEBUG_NEW`，用于替换**新**运算符时你需要文件和行号的内存分配的跟踪。 `DEBUG_NEW` 你通常应使用时，需要使用**新**运算符。  
  
 与其他诊断`CMemoryState`诊断程序仅在程序的调试版本中可用。 必须具有的调试版本 **_DEBUG**定义常量。  
  
 如果你怀疑你的程序有内存泄漏，则可以使用`Checkpoint`，**差异**，和`DumpStatistics`函数在程序中的两个不同点发现 （分配的对象） 的内存状态之间的差异执行。 此信息可以用于确定是否将函数清理其所分配的所有对象。  
  
 如果只需知道在分配和解除分配这种不平衡的出现位置未提供足够的信息，则可以使用`DumpAllObjectsSince`函数转储所有对象分配到在上一个调用`Checkpoint`。 此转储演示的分配、 源文件和已分配的对象的行顺序 (如果你使用`DEBUG_NEW`分配)，和派生类型的对象，它的地址以及其大小。 `DumpAllObjectsSince` 此外会调用每个对象的`Dump`函数提供有关其当前状态信息。  
  
 有关如何使用`CMemoryState`和其他诊断，请参阅[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。  
  
> [!NOTE]
>  类型的对象的声明`CMemoryState`和对成员函数的调用应通过括起来`#if defined(_DEBUG)/#endif`指令。 这会导致内存诊断，包括仅在调试程序的版本。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CMemoryState`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="checkpoint"></a>  CMemoryState::Checkpoint  
 拍摄快照的内存的摘要，并将其存储在此`CMemoryState`对象。  
  
```  
void Checkpoint();
```  
  
### <a name="remarks"></a>备注  
 `CMemoryState`成员函数[差异](#difference)和[DumpAllObjectsSince](#dumpallobjectssince)使用此快照数据。  
  
### <a name="example"></a>示例  
  请参阅示例[CMemoryState](#cmemorystate)构造函数。  
  
##  <a name="cmemorystate"></a>  CMemoryState::CMemoryState  
 构造一个空`CMemoryState`对象必须由填写[检查点](#checkpoint)或[差异](#difference)成员函数。  
  
```  
CMemoryState();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]  
  
##  <a name="difference"></a>  CMemoryState::Difference  
 比较两个`CMemoryState`对象，然后将存储到此差异`CMemoryState`对象。  
  
```  
BOOL Difference(
    const CMemoryState& oldState,   
    const CMemoryState& newState);
```  
  
### <a name="parameters"></a>参数  
 *oldState*  
 按照定义的初始内存状态`CMemoryState`检查点。  
  
 *newState*  
 通过定义新的内存状态`CMemoryState`检查点。  
  
### <a name="return-value"></a>返回值  
 如果这两个内存状态不同; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 [检查点](#checkpoint)必须为每个两个内存状态参数调用。  
  
### <a name="example"></a>示例  
  请参阅示例[CMemoryState](#cmemorystate)构造函数。  
  
##  <a name="dumpallobjectssince"></a>  Cmemorystate:: Dumpallobjectssince  
 调用`Dump`函数的所有对象类型的派生自类`CObject`，已分配了 （和仍分配） 自上次操作后[检查点](#checkpoint)调用此`CMemoryState`对象。  
  
```  
void DumpAllObjectsSince() const;

 
```  
  
### <a name="remarks"></a>备注  
 调用`DumpAllObjectsSince`使用未初始化`CMemoryState`对象将转储当前在内存中的所有对象。  
  
### <a name="example"></a>示例  
  请参阅示例[CMemoryState](#cmemorystate)构造函数。  
  
##  <a name="dumpstatistics"></a>  CMemoryState::DumpStatistics  
 输出中的简洁内存统计信息报告`CMemoryState`对象由填写[差异](#difference)成员函数。  
  
```  
void DumpStatistics() const;

 
```  
  
### <a name="remarks"></a>备注  
 报表打印[afxDump](diagnostic-services.md#afxdump)设备，显示以下：  
  
 示例报表提供了有关的数 （或量） 信息：  
  
-   可用块  
  
-   正常的块  
  
-   CRT 块  
  
-   忽略块  
  
-   客户端块  
  
-   在任何时候 （以字节为单位） 的程序所使用的最大内存  
  
-   当前使用的程序 （以字节为单位） 的总内存  
  
 可用块是指次数时，已延迟释放的块`afxMemDF`已设置为**delayFreeMemDF**。 有关详细信息，请参阅[afxMemDF](diagnostic-services.md#afxmemdf)，"MFC 宏和全局"部分中。 请参阅[调试堆上类型的块](http://msdn.microsoft.com/en-us/db2e7f62-0679-4b39-a23f-26f2c2f407c5)详细信息，这些块类型。  
  
### <a name="example"></a>示例  
  应将以下代码放置在*projname*app.cpp。 定义以下全局变量：  
  
 [!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]  
  
 在`InitInstance`函数中，添加行：  
  
 [!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]  
  
 添加的处理程序`ExitInstance`函数，并使用以下代码：  
  
 [!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]  
  
 你现在可以运行该程序在调试模式下，若要查看的输出`DumpStatistics`函数。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)



