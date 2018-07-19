---
title: .重复 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .REPEAT
dev_langs:
- C++
helpviewer_keywords:
- .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41e3dadaa95cb4bf0ca4a17af32332d5b5471245
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32052445"
---
# <a name="repeat"></a>.REPEAT
生成重复的块执行的代码*语句*直到`condition`而变为 true。 [.UNTILCXZ](../../assembler/masm/dot-untilcxz.md)，它将变为 true 时 CX 为零，可能替换为[。直到](../../assembler/masm/dot-until.md)。 `condition`是可选的 with **。UNTILCXZ**。  
  
## <a name="syntax"></a>语法  
  
```  
  
   .REPEAT  
statements  
.UNTIL condition  
```  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)