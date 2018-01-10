---
title: "-RAWDATA |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /rawdata
dev_langs: C++
helpviewer_keywords:
- RAWDATA dumpbin option
- raw data
- -RAWDATA dumpbin option
- /RAWDATA dumpbin option
ms.assetid: 41cba845-5e1f-415e-9fe4-604a52235983
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 475ec5a827a1453a6f9474762d5be41299fc87e4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="rawdata"></a>/RAWDATA
```  
/RAWDATA[:{1|2|4|8|NONE[,number]]  
```  
  
## <a name="remarks"></a>备注  
 此选项显示在文件中的每个部分的原始内容。 参数控制的格式显示，如下所示：  
  
|参数|结果|  
|--------------|------------|  
|1|默认值。 如果它们具有打印表示形式，内容将显示以十六进制字节为单位，以及为 ASCII 字符。|  
|2|内容将显示为十六进制的 2 字节值。|  
|4|内容将显示为 4 字节的十六进制值。|  
|8|内容将显示为 8 字节的十六进制值。|  
|无|取消显示原始数据。 此参数可用于控制的输出/全部。|  
|数字|显示的行设置为包含一个宽度`number`每行的值。|  
  
 仅[/HEADERS](../../build/reference/headers.md) DUMPBIN 选项是可供产生的文件的使用[/GL](../../build/reference/gl-whole-program-optimization.md)编译器选项。  
  
## <a name="see-also"></a>请参阅  
 [DUMPBIN 选项](../../build/reference/dumpbin-options.md)