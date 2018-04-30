---
title: ML 错误消息 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: fbc2ae6388ad11a411850d03de421d2f6820fc03
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="ml-error-messages"></a>ML 错误消息
MASM 组件生成的错误消息分为三个类别：  
  
-   **致命错误。** 这些警报表示严重问题，以防止该实用工具完成其正常的过程。  
  
-   **非致命错误。** 实用程序可能完成其进程。 如果是这样，其结果是不可能是所需的那个。  
  
-   **警告。** 这些邮件表示可能会阻止你获取所需的结果的条件。  
  
 所有的错误消息采用以下形式：  
  
```  
  
Utility: Filename (Line) : [Error_type} (Code): Message_text  
```  
  
 其中：  
  
 `Utility`  
 发送错误消息中的程序。  
  
 *文件名*  
 包含生成时出现错误条件的文件。  
  
 *Line*  
 在错误条件存在大致行。  
  
 *Error_type*  
 致命错误、 错误或警告。  
  
 *代码*  
 唯一的 5 或 6 位错误代码。  
  
 `Message_text`  
 短期和常规错误条件的说明。  
  
## <a name="see-also"></a>请参阅  
 [Microsoft 宏汇编程序参考](../../assembler/masm/microsoft-macro-assembler-reference.md)