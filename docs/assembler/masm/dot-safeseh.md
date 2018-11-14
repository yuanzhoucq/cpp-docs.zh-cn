---
title: .SAFESEH
ms.date: 08/30/2018
f1_keywords:
- .SAFESEH
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
ms.openlocfilehash: 417aea13518621f775cafa176ff7d74f9704d511
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328352"
---
# <a name="safeseh"></a>.SAFESEH

为结构化的异常处理程序注册的函数。

## <a name="syntax"></a>语法

> .SAFESEH 标识符

## <a name="remarks"></a>备注

*标识符*必须是本地定义的 ID [PROC](../../assembler/masm/proc.md)或[EXTRN](../../assembler/masm/extrn.md)过程。 一个[标签](../../assembler/masm/label-masm.md)不允许。 。SAFESEH 指令需要[/safeseh](../../assembler/masm/ml-and-ml64-command-line-reference.md) ml.exe 命令行选项。

有关结构化的异常处理程序的详细信息，请参阅[/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)。

例如，若要注册的安全异常处理程序，（按如下所示） 创建一个新的 MASM 文件、 组合使用 /safeseh，并将其添加到链接的对象。

```asm
.386
.model  flat
MyHandler   proto
.safeseh    MyHandler
end
```

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>