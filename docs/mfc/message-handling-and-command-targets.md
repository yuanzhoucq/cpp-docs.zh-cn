---
title: 消息处理和命令目标 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61ed4375121dafe198dce84b155858c0e7b0a8cb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414142"
---
# <a name="message-handling-and-command-targets"></a>消息处理和命令目标

命令调度接口`IOleCommandTarget`定义查询和执行命令的简单且可扩展的机制。 此机制是比自动化的简单`IDispatch`因为它依赖于一组标准的命令; 完全命令很少能有参数，且涉及无类型信息 （类型安全性降低了命令的参数）。

在命令调度接口设计，每个命令都属于"命令组"本身标识与**GUID**。 因此，任何人都可以定义新的组，并定义而无需任何需要与 Microsoft 进行协调或任何其他供应商该组中的所有命令。 (这是实质上是相同的定义作为平均值**dispinterface**加上**Dispid**在自动化中。 不存在重叠，尽管此命令路由机制作为自动化句柄是仅用于命令路由而不用于大规模脚本撰写和编程。）

`IOleCommandTarget` 处理以下方案：

- 一个对象时就地激活，通常显示对象的工具栏和对象的工具栏可能就一些类似的容器命令的按钮仅**打印**，**打印预览**， **保存**，**新建**，**缩放**，等等。 （在就地激活标准建议对象删除此类按钮从其工具栏，或在至少禁用它们。 此设计允许这些命令来启用和尚未路由到正确的处理程序。）目前，没有要调度到容器的这些命令的对象的机制。

- 当在活动文档容器 （如 Office 活页夹） 中嵌入活动文档时，容器可能需要将命令发送此类**打印**，**页面设置**，**属性**，和其他包含的活动文档。

可以通过现有的自动化标准处理这种简单的命令路由和`IDispatch`。 但是，与涉及的开销`IDispatch`多于这，因此`IOleCommandTarget`提供更简单的方法来实现同样的目的：

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

`QueryStatus`此处方法测试一组特定的命令，该集正在使用标识是否**GUID**，支持。 此调用填充的数组**OLECMD**支持的命令，以及返回的文字描述命令和/或状态信息的名称，列表的值 （结构）。 当调用方想要调用命令时，它可以传递命令 (和集**GUID**) 到`Exec`选项和参数，以及获取返回值。

## <a name="see-also"></a>请参阅

[活动文档容器](../mfc/active-document-containers.md)

