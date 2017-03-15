---
title: "CMemoryState 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMemoryState
dev_langs:
- C++
helpviewer_keywords:
- CMemoryState structure
- memory leaks, detecting
- detecting memory leaks
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 037c8f075a14346e3428c5e19bfda662c4f3c2b0
ms.lasthandoff: 02/24/2017

---
# <a name="cmemorystate-structure"></a>CMemoryState 结构
提供了简便的方法来检测您的程序中的内存泄漏。  
  
## <a name="syntax"></a>语法  
  
```  
struct CMemoryState  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMemoryState::CMemoryState](#cmemorystate)|构造类状结构，它控制内存检查点。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMemoryState::Checkpoint](#checkpoint)|获取当前内存状态的快照 （检查点）。|  
|[CMemoryState::Difference](#difference)|计算类型的两个对象之间的差`CMemoryState`。|  
|[CMemoryState::DumpAllObjectsSince](#dumpallobjectssince)|自上一个检查点以来转储所有当前已分配对象的摘要。|  
|[CMemoryState::DumpStatistics](#dumpstatistics)|打印内存分配统计信息`CMemoryState`对象。|  
  
## <a name="remarks"></a>备注  
 `CMemoryState`是一种结构，并且没有基类的类。  
  
 对象的内存是在堆上分配但未释放不再需要时，会发生"内存泄漏"。 此类内存泄漏可能最终导致内存不足错误。 有几种方法来分配和释放程序中的内存︰  
  
-   使用`malloc` / **免费**系列的函数的运行时库。  
  
-   使用 Windows API 内存管理函数， **LocalAlloc**/ **LocalFree**和**GlobalAlloc**/ **GlobalFree**。  
  
-   使用 c + +**新**和**删除**运算符。  
  
 `CMemoryState`诊断不仅帮助检测内存泄漏时使用的内存分配导致**新**运算符未释放使用**删除**。 内存管理函数中的其他两个组适用于非 c + + 程序，并将它们与混合**新**和**删除**不建议在同一个程序。 存在其他宏`DEBUG_NEW`，可用于替换**新**运算符在您需要文件和行号的内存分配的跟踪。 `DEBUG_NEW`你通常应使用时，需要使用**新**运算符。  
  
 与其他诊断`CMemoryState`诊断程序仅在程序的调试版本中可用。 调试版本都必须有**_DEBUG**定义的常量。  
  
 如果您怀疑您的程序有内存泄漏，则可以使用`Checkpoint`，**差异**，和`DumpStatistics`函数在程序执行两个不同时间点上发现的内存状态 （已分配的对象） 之间的差异。 此信息可能有助于确定函数是否清除其所分配的所有对象。  
  
 如果只需了解这种不平衡分配和解除分配中的出现的位置未提供足够的信息，则可以使用`DumpAllObjectsSince`函数来转储自上次调用以来分配的所有对象`Checkpoint`。 该转储显示了分配、 源文件和行分配的对象的顺序 (如果您使用`DEBUG_NEW`分配)，与派生的对象、 它的地址，以及其大小。 `DumpAllObjectsSince`此外会调用每个对象的`Dump`函数以提供有关其当前状态的信息。  
  
 有关如何使用`CMemoryState`和其他诊断，请参见[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。  
  
> [!NOTE]
>  声明类型的对象的`CMemoryState`和对成员函数的调用应括起来的`#if defined(_DEBUG)/#endif`指令。 这会导致内存诊断功能可以包含只在调试生成您的程序。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CMemoryState`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="a-namecheckpointa--cmemorystatecheckpoint"></a><a name="checkpoint"></a>CMemoryState::Checkpoint  
 获取快照摘要的内存，并将其存储在此`CMemoryState`对象。  
  
```  
void Checkpoint();
```  
  
### <a name="remarks"></a>备注  
 `CMemoryState`成员函数[差异](#difference)和[DumpAllObjectsSince](#dumpallobjectssince)使用此快照数据。  
  
### <a name="example"></a>示例  
  请参阅示例[CMemoryState](#cmemorystate)构造函数。  
  
##  <a name="a-namecmemorystatea--cmemorystatecmemorystate"></a><a name="cmemorystate"></a>CMemoryState::CMemoryState  
 构造一个空`CMemoryState`对象，它必须通过填写[检查点](#checkpoint)或[差异](#difference)成员函数。  
  
```  
CMemoryState();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities #&18;](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]  
  
##  <a name="a-namedifferencea--cmemorystatedifference"></a><a name="difference"></a>CMemoryState::Difference  
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
 如果这两个内存状态不同; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 [检查点](#checkpoint)必须已为两个内存状态参数的每个调用。  
  
### <a name="example"></a>示例  
  请参阅示例[CMemoryState](#cmemorystate)构造函数。  
  
##  <a name="a-namedumpallobjectssincea--cmemorystatedumpallobjectssince"></a><a name="dumpallobjectssince"></a>CMemoryState::DumpAllObjectsSince  
 调用`Dump`从类派生的类型的所有对象的函数`CObject`，所分配 （和仍分配） 自上次[检查点](#checkpoint)调用此`CMemoryState`对象。  
  
```  
void DumpAllObjectsSince() const;

 
```  
  
### <a name="remarks"></a>备注  
 调用`DumpAllObjectsSince`使用未初始化`CMemoryState`对象将转储当前在内存中的所有对象。  
  
### <a name="example"></a>示例  
  请参阅示例[CMemoryState](#cmemorystate)构造函数。  
  
##  <a name="a-namedumpstatisticsa--cmemorystatedumpstatistics"></a><a name="dumpstatistics"></a>CMemoryState::DumpStatistics  
 打印从的简洁内存统计信息报告`CMemoryState`对象，它由填充[差异](#difference)成员函数。  
  
```  
void DumpStatistics() const;

 
```  
  
### <a name="remarks"></a>备注  
 报表打印[afxDump](http://msdn.microsoft.com/library/4b3cfa3f-fb75-456a-9d99-a5601acbcb11)设备上，显示以下︰  
  
 示例报表提供有关信息的数字 （或量）︰  
  
-   可用块  
  
-   普通块  
  
-   CRT 块  
  
-   忽略块  
  
-   客户端块  
  
-   在任何一个时间 （以字节为单位） 使用的程序的最大内存  
  
-   （以字节为单位） 的程序当前使用的内存总量  
  
 可用块是如果时延迟释放的块的数目`afxMemDF`已设置为**delayFreeMemDF**。 有关详细信息，请参阅[afxMemDF](diagnostic-services.md#afxmemdf)，"MFC 宏和全局变量"部分中。 请参阅[调试堆上类型的块](http://msdn.microsoft.com/en-us/db2e7f62-0679-4b39-a23f-26f2c2f407c5)的详细信息，这些块类型。  
  
### <a name="example"></a>示例  
  下面的代码应置于*projname*app.cpp。 定义以下全局变量︰  
  
 [!code-cpp[NVC_MFC_Utilities #&40;](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]  
  
 在`InitInstance`函数中，添加行︰  
  
 [!code-cpp[NVC_MFC_Utilities #&41;](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]  
  
 添加处理程序`ExitInstance`函数，并使用以下代码︰  
  
 [!code-cpp[NVC_MFC_Utilities #&42;](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]  
  
 您现在可以运行该程序在调试模式下，若要查看的输出`DumpStatistics`函数。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)




