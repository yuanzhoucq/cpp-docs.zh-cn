---
title: ML 错误消息
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- vc.errors.ml
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
ms.openlocfilehash: adf2c509c3d8d9110ddb757f809a4bca9199df7a
ms.sourcegitcommit: af580f3a11b19d22288424eac7ceae1bc24ab312
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "66355330"
---
# <a name="ml-error-messages"></a>ML 错误消息

MASM 组件生成的错误消息划分为三个类别：

- **严重错误。** 这些警报表示严重问题，以防止该实用程序完成其正常的过程。

- **非致命错误。** 该实用程序可能会完成其进程。 如果是这样，其结果是不可能是所需的一个。

- **警告。** 这些消息指示可能会阻止你获取所需的结果的条件。

所有错误消息都采用以下格式：

> *实用工具*:*文件名*(*行*): {*Error_type*} (*代码*):*Message_text*

其中：

*实用工具*<br/>
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

[Microsoft 宏汇编程序参考](../../assembler/masm/microsoft-macro-assembler-reference.md)
