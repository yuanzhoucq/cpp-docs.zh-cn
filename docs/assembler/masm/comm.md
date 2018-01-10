---
title: "COMM |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: COMM
dev_langs: C++
helpviewer_keywords: COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ad12de948227f98ec73f779030b8e644dfad8b2c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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