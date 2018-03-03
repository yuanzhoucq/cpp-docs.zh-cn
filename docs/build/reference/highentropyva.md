---
title: "-HIGHENTROPYVA |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /HIGHENTROPYVA
dev_langs:
- C++
helpviewer_keywords:
- HIGHENTROPYVA editbin option
- -HIGHENTROPYVA editbin option
- /HIGHENTROPYVA editbin option
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 36ca3ea93f494587663d863b1dc4646750d38e82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="highentropyva"></a>/HIGHENTROPYVA
指定可执行映像是否支持高熵 64 位地址空间布局随机化 (ASLR)。  
  
```  
  
/HIGHENTROPYVA[:NO]  
```  
  
## <a name="remarks"></a>备注  
 此选项修改 .dll 文件或 .exe 文件的标头，以指示是否支持 64 位地址的 ASLR。 当在可执行文件和所有依赖的模块上执行此选项时，支持 64 位 ASLR 的操作系统可在加载时通过使用 64 位虚拟地址空间来变基可执行映像。 更大的地址空间使攻击者更难猜到特定内存区域的位置。  
  
 默认情况下，链接器为 64 位可执行映像设置此选项。 若要设置此选项， [/DYNAMICBASE](../../build/reference/dynamicbase.md)还必须设置选项。  
  
## <a name="see-also"></a>请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)   
 [/DYNAMICBASE](../../build/reference/dynamicbase.md)   
 [Windows ISV 软件安全防御措施](http://msdn.microsoft.com/library/bb430720.aspx)