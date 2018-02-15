---
title: "ML 错误 A1017 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- A1017
dev_langs:
- C++
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3f77f6d2905d70614735beb6cbcefeeb7e07b491
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="ml-fatal-error-a1017"></a>ML 错误 A1017
**缺少源 filename**  
  
 ML 找不到要装配或传递给链接器的文件。  
  
 当你向 ML 命令行选项而无需指定文件名以执行操作，则会生成此错误。 若要将组合不具有.asm 扩展名的文件，使用**/Ta**命令行选项。  
  
 此外可以通过调用 ML 不带任何参数，如果 ML 环境变量包含命令行选项生成此错误。  
  
## <a name="see-also"></a>请参阅  
 [ML 错误消息](../../assembler/masm/ml-error-messages.md)