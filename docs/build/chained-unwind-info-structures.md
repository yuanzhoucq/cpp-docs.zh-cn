---
title: "链式展开信息结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 176835bf-f118-45d9-9128-9db4b7571864
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3ac09c1f107b51542b7a17c8661eb784b4abf14a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="chained-unwind-info-structures"></a>链式展开信息结构
如果设置 UNW_FLAG_CHAININFO 标志，然后展开信息结构是一个辅助和共享的异常的处理程序/链接的信息地址字段包含主展开信息。 以下代码检索主展开信息，假定`unwindInfo`是具有 UNW_FLAG_CHAININFO 结构标志设置。  
  
```  
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);  
```  
  
 链接的信息可在两种情况下。 首先，它可以用于非连续代码段。 通过使用链接的信息，你可以减少需要的展开信息中的大小，因为无需重复主展开信息中的展开代码数组。  
  
 你还可以使用链接的信息将易失寄存器保存。 编译器可能会延迟超出函数项 prolog 之前保存某些易失寄存器。 记录分组的代码中之前, 提供函数的部分的主展开信息这，然后设置链式的序言中，其中链式信息中的展开代码反映的非易失寄存器保存的非零大小的信息。 在这种情况下，展开代码是 UWOP_SAVE_NONVOL 的所有实例。 不支持的分组，它将非易失寄存器保存通过推送或使用其他固定的堆栈分配修改 RSP 注册。  
  
 Unwind_info 结构项具有 UNW_FLAG_CHAININFO 设置可以包含其 unwind_info 结构项也具有 UNW_FLAG_CHAININFO 设置 （多个紧缩套装） runtime_function 结构项。 最终，连锁展开指针将到达具有 UNW_FLAG_CHAININFO 清除; 的 unwind_info 结构项目的信息这是指向实际过程入口点的主 unwind_info 结构项。  
  
## <a name="see-also"></a>请参阅  
 [为异常处理和调试器支持展开数据](../build/unwind-data-for-exception-handling-debugger-support.md)