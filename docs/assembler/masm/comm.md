---
title: COMM |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- COMM
dev_langs:
- C++
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 111dac47089fea13febe787e5b73557b287beea8
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="comm"></a>COMM
与在指定的属性创建一个公用变量`definition`。  
  
## <a name="syntax"></a>语法  
  
```  
  
COMM definition [[, definition]] ...  
```  
  
## <a name="remarks"></a>备注  
 每个`definition`具有以下形式：  
  
 [[*langtype*]] [[**NEAR** &#124; **远处**]]*标签 ***:**`type`[[**:*** 计数*]]  
  
 *标签*是变量的名称。 `type`可以是任何类型说明符 ([字节](../../assembler/masm/byte-masm.md)， [WORD](../../assembler/masm/word.md)，依次类推) 或一个整数，指定的字节数。 *计数*指定 （之一是默认值） 的数据对象的数目。  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)