---
title: COMM | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COMM
dev_langs:
- C++
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6258a584d39f598b32c43affc0ef2569b77b2047
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="comm"></a>COMM
与在指定的属性创建一个公用变量`definition`。  
  
## <a name="syntax"></a>语法  
  
```  
  
COMM definition [[, definition]] ...  
```  
  
## <a name="remarks"></a>备注  
 每个`definition`具有以下形式：  
  
 [[*langtype*]] [[**NEAR** &#124;**远处**]]*标签***:**`type`[[**:***计数*]]  
  
 *标签*是变量的名称。 `type`可以是任何类型说明符 ([字节](../../assembler/masm/byte-masm.md)， [WORD](../../assembler/masm/word.md)，依次类推) 或一个整数，指定的字节数。 *计数*指定 （之一是默认值） 的数据对象的数目。  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)