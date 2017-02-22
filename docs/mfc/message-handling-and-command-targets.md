---
title: "消息处理和命令目标 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IOleCommandTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令传送, 命令目标"
  - "命令目标"
  - "IOleCommandTarget 接口"
  - "消息处理, 活动文档"
ms.assetid: e45ce14c-e6b6-4262-8f3b-4e891e0ec2a3
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 消息处理和命令目标
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

命令安排 `IOleCommandTarget` 接口定义一个简单的可扩展机制查询和执行命令。  因为它完全取决于标准的命令，此机制比简单自动化的 `IDispatch` ;命令最少有参数，而且，类型信息而不是包含类型 \(安全性为命令参数减少\)。  
  
 在命令调度接口设计，每个命令属于自己使用 **GUID**标识“命令组”。  因此，无论在该组中可以定义新组和定义所有命令，而无需任何需要与 Microsoft 或其他供应商。\(这在本质上是定义与 **dispinterface** 相同表示以及在自动的 **dispIDs**。  存在重叠，其中，尽管此路由命令机制规模可仅用于。命令传送和不为脚本\/可编程性用作自动化句柄。\)  
  
 `IOleCommandTarget` 处理以下情况：  
  
-   当对象是就地激活，因此，只有对象的工具栏通常显示对象的和工具栏可能具有特定的按钮与 **打印打印**、**预览**，**保存**、`New`时，**缩放**和其他命令的容器。\(标准对象就地激活建议从它们的工具栏这样的按钮或至少会禁用它们。  此设计允许启用这些命令，仍将路由到正确的处理程序。\)目前，此对象没有机制可以将这些命令的容器。  
  
-   在活动文档处于活动文档容器 \(例如容器\) 嵌入 Office 活页夹，可能需要这样将命令发送 **打印**、**页 安装**，为 **属性**和其他包含的活动文档。  
  
 此简单命令传送可以通过现有自动标准和 `IDispatch`进行处理。  但是，系统开销与 `IDispatch` 比需要几个否认更多，因此，`IOleCommandTarget` 提供更简单方式实现相同的用途：  
  
 `interface IOleCommandTarget : IUnknown`  
  
 `{`  
  
 `HRESULT QueryStatus(`  
  
 `[in] GUID *pguidCmdGroup,`  
  
 `[in] ULONG cCmds,`  
  
 `[in,out][size_is(cCmds)] OLECMD *prgCmds,`  
  
 `[in,out] OLECMDTEXT *pCmdText);`  
  
 `HRESULT Exec(`  
  
 `[in] GUID *pguidCmdGroup,`  
  
 `[in] DWORD nCmdID,`  
  
 `[in] DWORD nCmdExecOpt,`  
  
 `[in] VARIANTARG *pvaIn,`  
  
 `[in,out] VARIANTARG *pvaOut);`  
  
 `}`  
  
 这里 `QueryStatus` 方法测试特定组命令，标识与 **GUID**，是否支持。  此调用填充 **OLECMD** 值 \(结构\) 与支持命令的列表以及返回描述命令和状态信息的名称的文本。  当调用方希望调用命令时，它可将命令传递 \(集合\) 和 **GUID**为 **Exec**，以及选项和参数。获取返回返回值。  
  
## 请参阅  
 [活动文档容器](../mfc/active-document-containers.md)