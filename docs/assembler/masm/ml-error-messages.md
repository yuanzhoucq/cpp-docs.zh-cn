---
title: ML 错误消息 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- vc.errors.ml
dev_langs:
- C++
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 836daf438fa5a7f4c797b5b15ffab89720a7af98
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43675960"
---
# <a name="ml-error-messages"></a>ML 错误消息

MASM 组件生成的错误消息划分为三个类别：

- **严重错误。** 这些警报表示严重问题，以防止该实用程序完成其正常的过程。

- **非致命错误。** 该实用程序可能会完成其进程。 如果是这样，其结果是不可能是所需的一个。

- **警告。** 这些消息指示可能会阻止你获取所需的结果的条件。

所有错误消息都采用以下格式：

> *实用工具*:*文件名*(*行*): {*Error_type*} (*代码*): *Message_text*

其中：

*实用程序*<br/>
发送错误消息中的程序。

*文件名*<br/>
包含生成错误的条件的文件。

*Line*<br/>
存在错误条件的近似行。

*Error_type*<br/>
致命错误、 错误或警告。

*代码*<br/>
唯一的 5 或 6 位错误代码。

*Message_text*<br/>
短期和常规错误条件的说明。

## <a name="see-also"></a>请参阅

[Microsoft 宏汇编程序参考](../../assembler/masm/microsoft-macro-assembler-reference.md)<br/>