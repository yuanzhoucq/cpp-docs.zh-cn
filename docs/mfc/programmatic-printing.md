---
title: "以编程方式打印 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "活动文档 [C++], 打印"
  - "IPrint 接口"
  - "打印 [MFC]"
  - "打印 [MFC], 活动文档"
  - "打印 [MFC], 编程"
ms.assetid: 3db0945b-5e13-4be4-86a0-6aecdae565bd
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 以编程方式打印
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

OLE 提供了唯一标识不文档 \(**GetClassFile**\) 并加载它们到的代码关联 \(`CoCreateInstance`、 **QueryInterface\(IID\_IPersistFile\)**、 **QueryInterface\(IID\_IPersistStorage\)**、 **IPersistFile::Load**和 **IPersistStorage::Load**\)。  进一步启用打印文档，活动文档包容 \(使用一种现有的 OLE 设计最初未附带 OLE 2.0 引入\) 标准的打印基本接口， `IPrint` 通常，活动将能加载文档类型中持久状态的所有对象。  活动文档视图的每个可以选择支持 **IPrint** 接口提供这些功能。  
  
 该 `IPrint` 接口定义如下：  
  
 `interface IPrint : IUnknown`  
  
 `{`  
  
 `HRESULT SetInitialPageNum([in] LONG nFirstPage);`  
  
 `HRESULT GetPageInfo(`  
  
 `[out] LONG *pnFirstPage,`  
  
 `[out] LONG *pcPages);`  
  
 `HRESULT Print(`  
  
 `[in] DWORD grfFlags,`  
  
 `[in,out] DVTARGETDEVICE **pptd,`  
  
 `[in,out] PAGESET ** ppPageSet,`  
  
 `[in,out] STGMEDIUM **ppstgmOptions,`  
  
 `[in] IContinueCallback* pCallback,`  
  
 `[in] LONG nFirstPage,`  
  
 `[out] LONG *pcPagesPrinted,`  
  
 `[out] LONG *pnPageLast);`  
  
 `};`  
  
 客户和容器使用 **IPrint::Print** 指示文档打印文档加载，打印一次指定控制标志，目标设备、页以及其他选项。  客户端只能通过 `IContinueCallback` 接口来控制文档打印的继续 \(如下所示\)。  
  
 此外，支持 **IPrint::SetInitialPageNum** 能够打印文档一系列，当一个页是通过计算无缝，对活动文档容器的一个优点明确想 Office 活页夹。  **IPrint::GetPageInfo** 使显示的分页信息简单通过允许调用方检索启动的页数之前传递到 **SetInitialPageNum** \(或启动的页数\) 文档的内部默认和的页数文档中。  
  
 支持 `IPrint` 对象中的“可打印的”密钥的注册表中标记存储在对象的 CLSID 下：  
  
 HKEY\_CLASSES\_ROOT\\CLSID\\{...}\\Printable  
  
 `IPrint` 支持 `IPersistFile` 或 `IPersistStorage`的同一对象通常实现。  调用方通过编程方式发现打印功能注意一些类的持久状态在注册表“可打印的”键的。  目前，“可打印”指示至少支持 `IPrint`;然后通过 `QueryInterface` 可由 **IPrint** 表示基本支持级别的任何其他接口可能在以后定义。  
  
 在打印的过程中，您可能希望启动打印控制的客户或容器打印指定是否应继续。  例如，可以支持容器应尽快停止打印作业的“停止打印”命令。  为了支持此功能，可打印的对象的客户端可以与实现 `IContinueCallback`接口的一小的通知接收器对象：  
  
 `interface IContinueCallback : IUnknown`  
  
 `{`  
  
 `HRESULT FContinue(void);`  
  
 `HRESULT FContinuePrinting(`  
  
 `[in] LONG cPagesPrinted,`  
  
 `[in] LONG nCurrentPage,`  
  
 `[in] LPOLESTR pszPrintStatus);`  
  
 `};`  
  
 此接口旨在将用作将取代在 Win32 API 的各个过程继续的一般性继续回调函数 \(如打印的 **AbortProc** 和元文件枚举的 **EnumMetafileProc** \)。  因此此接口设计为适用于多种耗时的过程。  
  
 在最常规的情况下， **IContinueCallback::FContinue** 函数。所有长进程定期调用。  接收器对象返回 `S_OK` **S\_FALSE** 继续操作并尽快停止过程。  
  
 **FContinue**，但是，不使用 **IPrint::Print**;上下文中相比之下，print 使用 **IContinueCallback::FContinuePrint**。  所有打印的对象应定期调用传递打印的页数，页的数字打印和其他的字符串的 **FContinuePrinting** 说明客户可以选择向用户显示打印的状态 \(如分页“5 19 "\)。  
  
## 请参阅  
 [活动文档容器](../mfc/active-document-containers.md)