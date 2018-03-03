---
title: "消息处理和命令目标 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IOleCommandTarget
dev_langs:
- C++
helpviewer_keywords:
- command targets [MFC]
- message handling [MFC], active documents
- IOleCommandTarget interface [MFC]
- command routing [MFC], command targets
ms.assetid: e45ce14c-e6b6-4262-8f3b-4e891e0ec2a3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 81ec1f2a1f419715a3e8e9fbac2fcba3c7584a9b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="message-handling-and-command-targets"></a>消息处理和命令目标
命令调度接口`IOleCommandTarget`定义一种简单和可扩展的机制，以查询和执行命令。 此机制是比自动化的简单得多`IDispatch`因为它依赖于一组标准的命令; 完全命令很少具有参数，且涉及无类型信息 （命令自变量也会降低类型安全）。  
  
 在命令调度接口设计中，每个命令都属于本身识别具有"命令组" **GUID**。 因此，任何人都可以定义新的组，并定义而无需任何需要与 Microsoft 进行协调或任何其他供应商该组中的所有命令。 (这是实质上与定义的相同方式**调度接口**加上**Dispid**自动化中。 没有重叠在这里，尽管此命令路由机制作为自动化句柄是仅用于命令路由而不是针对大规模脚本/可编程性。）  
  
 `IOleCommandTarget`处理以下方案：  
  
-   一个对象时就地激活，仅通常显示对象的工具栏，该对象的工具栏可能有按钮等容器命令的某些**打印**，**打印预览**， **保存**， `New`，**缩放**，和其他人。 （在就地激活标准建议对象删除此类按钮从其工具栏中，或在至少禁用它们。 此设计允许这些命令来启用和尚未路由到正确的处理程序。）目前，没有任何机制可要调度到容器中的这些命令的对象。  
  
-   当在活动文档容器 （如 Office 活页夹） 中嵌入活动文档时，容器可能需要将命令发送此类**打印**，**页面设置**，**属性**，和其他包含的活动文档。  
  
 通过现有的自动化标准无法处理此简单的命令路由和`IDispatch`。 但是，与涉及的开销`IDispatch`高于此，有必要对以便`IOleCommandTarget`提供一种更简单的方式来实现同一目的：  
  
```  
interface IOleCommandTarget : IUnknown  
    {  
    HRESULT QueryStatus(  
        [in] GUID *pguidCmdGroup,  
        [in] ULONG cCmds,  
        [in,out][size_is(cCmds)] OLECMD *prgCmds,  
        [in,out] OLECMDTEXT *pCmdText);  
    HRESULT Exec(  
        [in] GUID *pguidCmdGroup,  
        [in] DWORD nCmdID,  
        [in] DWORD nCmdExecOpt,  
        [in] VARIANTARG *pvaIn,  
        [in,out] VARIANTARG *pvaOut);  
    }  
```  
  
 `QueryStatus`此处方法测试是否集正在使用标识一组特定的命令， **GUID**，支持。 此调用填充数组**OLECMD**与受支持的命令以及返回的文字描述命令和/或状态信息的名称，列表的值 （结构）。 当调用方想要调用的命令时，它可以传递命令 (和集**GUID**) 到**Exec**选项和自变量，以及获取返回值。  
  
## <a name="see-also"></a>请参阅  
 [活动文档容器](../mfc/active-document-containers.md)

