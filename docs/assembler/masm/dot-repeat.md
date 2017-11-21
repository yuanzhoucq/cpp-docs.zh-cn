---
title: ".重复 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .REPEAT
dev_langs: C++
helpviewer_keywords: .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e60ae387ec619a0109b322902a4ad40c9ad73f1e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="repeat"></a>.REPEAT
生成重复的块执行的代码*语句*直到`condition`而变为 true。 [.UNTILCXZ](../../assembler/masm/dot-untilcxz.md)，它将变为 true 时 CX 为零，可能替换为[。直到](../../assembler/masm/dot-until.md)。 `condition`是可选的 with **。UNTILCXZ**。  
  
## <a name="syntax"></a>语法  
  
```  
  
   .REPEAT  
statements  
.UNTIL condition  
```  
  
## <a name="see-also"></a>另请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)