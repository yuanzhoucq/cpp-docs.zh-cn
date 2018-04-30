---
title: ML 错误 A1017 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1017
dev_langs:
- C++
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5fcb2d921a40b35c6022b2aca1e22adc2d8c45e
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="ml-fatal-error-a1017"></a>ML 错误 A1017
**缺少源 filename**  
  
 ML 找不到要装配或传递给链接器的文件。  
  
 当你向 ML 命令行选项而无需指定文件名以执行操作，则会生成此错误。 若要将组合不具有.asm 扩展名的文件，使用 **/Ta**命令行选项。  
  
 此外可以通过调用 ML 不带任何参数，如果 ML 环境变量包含命令行选项生成此错误。  
  
## <a name="see-also"></a>请参阅  
 [ML 错误消息](../../assembler/masm/ml-error-messages.md)