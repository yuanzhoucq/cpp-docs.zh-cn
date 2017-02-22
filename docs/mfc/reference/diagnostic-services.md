---
title: "诊断服务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "诊断, 诊断函数和变量"
  - "诊断, 诊断服务"
  - "诊断, 常规 MFC 的列表"
  - "诊断函数和变量"
  - "诊断宏"
  - "诊断宏, 常规 MFC 的列表"
  - "诊断服务"
  - "诊断, 诊断函数和变量"
  - "诊断, 诊断服务"
  - "诊断, 常规 MFC 的列表"
  - "常规诊断函数和变量"
  - "MFC 中的常规诊断宏"
  - "MFC, 诊断服务"
  - "MFC 中的对象诊断函数"
  - "服务, 诊断"
ms.assetid: 8d78454f-9fae-49c2-88c9-d3fabd5393e8
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# 诊断服务
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Microsoft 基础类库提供了很多简化调试程序的诊断服务。 这些诊断服务包括宏和全局函数，让你能够跟踪程序的内存分配，在运行时转储对象的内容并打印调试消息。 诊断服务的宏和全局函数可分为以下几类：  
  
-   常规诊断宏  
  
-   常规诊断函数和变量  
  
-   对象诊断函数  
  
 这些宏和函数可用于派生自 MFC 调试和发布版本中的 `CObject` 的所有类。 但是，除 `DEBUG_NEW` 和 **VERIFY** 之外，它们在发布版本中不执行任何操作。  
  
 在调试库中，所有分配的内存块被一系列的“保护字节”包围。 如果这些字节受到错误内存写入的干扰，诊断例程可以报告问题。 如果包括行：  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/CPP/diagnostic-services_1.cpp)]  
  
 在实现文件中，所有对 **new** 的调用将存储发生内存分配的文件名和行号。 函数 [CMemoryState::DumpAllObjectsSince](../Topic/CMemoryState::DumpAllObjectsSince.md) 将显示此附加信息，帮助你确定内存泄漏。 关于诊断输出的其他信息，另请参阅 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 类。  
  
 此外，C 运行时库还支持一组可用于调试应用程序的诊断函数。 有关详细信息，请参阅《运行时库参考》中的[调试例程](../../c-runtime-library/debug-routines.md)。  
  
### MFC 常规诊断宏  
  
|||  
|-|-|  
|[ASSERT](../Topic/ASSERT%20\(MFC\).md)|如果库调试版本中的指定表达式的计算结果为 **FALSE**，则打印一条消息，然后中止程序。|  
|[ASSERT\_KINDOF](../Topic/ASSERT_KINDOF.md)|测试对象是指定类的对象还是指定类派生类的对象。|  
|[ASSERT\_VALID](../Topic/ASSERT_VALID.md)|通过调用 `AssertValid` 成员函数测试一个对象的内部有效性；通常从 `CObject` 中重写。|  
|[DEBUG\_NEW](../Topic/DEBUG_NEW.md)|提供调试模式下用于所有对象分配的文件名和行号以帮助查找内存泄漏。|  
|[DEBUG\_ONLY](../Topic/DEBUG_ONLY.md)|类似于 **ASSERT** 但不会测试表达式的值；对仅在调试模式下执行的代码非常有用。|  
|[TRACE](../Topic/TRACE.md)|在库调试版本中提供类似 `printf` 的功能。|  
|[VERIFY](../Topic/VERIFY.md)|类似于 **ASSERT**，但是可在库发布版本以及调试版本中计算表达式的值。|  
  
### MFC 常规诊断变量和函数  
  
|||  
|-|-|  
|[afxDump](../Topic/afxDump%20\(CDumpContext%20in%20MFC\).md)|将 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 信息发送给调试器输出窗口或调试终端的全局变量。|  
|[afxMemDF](../Topic/afxMemDF.md)|控制调试内存分配器行为的全局变量。|  
|[AfxCheckError](../Topic/AfxCheckError.md)|用于测试传递的 **SCODE** 是否出错的全局变量，如果出错，将引发相应的错误。|  
|[AfxCheckMemory](../Topic/AfxCheckMemory.md)|检查所有当前分配的内存的完整性。|  
|[AfxDump](../Topic/AfxDump%20\(MFC\).md)|如果在调试器中调用，将在调试时转储对象的状态。|  
|[AfxDumpStack](../Topic/AfxDumpStack.md)|生成当前堆栈的映像。 此函数始终以静态方式链接。|  
|[AfxEnableMemoryLeakDump](../Topic/AfxEnableMemoryLeakDump.md)|启用内存泄漏转储。|  
|[AfxEnableMemoryTracking](../Topic/AfxEnableMemoryTracking.md)|打开和关闭内存跟踪。|  
|[AfxIsMemoryBlock](../Topic/AfxIsMemoryBlock.md)|验证内存块是否正确分配。|  
|[AfxIsValidAddress](../Topic/AfxIsValidAddress.md)|验证内存地址范围是否在程序边界内。|  
|[AfxIsValidString](../Topic/AfxIsValidString.md)|确定一个字符串指针是否有效。|  
|[AfxSetAllocHook](../Topic/AfxSetAllocHook.md)|实现每次内存分配的函数调用。|  
  
### MFC 对象诊断函数  
  
|||  
|-|-|  
|[AfxDoForAllClasses](../Topic/AfxDoForAllClasses.md)|对支持运行时类型检查的所有 `CObject` 派生类执行指定函数。|  
|[AfxDoForAllObjects](../Topic/AfxDoForAllObjects.md)|对分配 **new** 的所有 `CObject` 派生对象执行指定函数。|  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)