---
title: EXTERN (MASM) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- extern
dev_langs:
- C++
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7528ea78270e4976ed3b926e83fe4f9977148498
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32054024"
---
# <a name="extern-masm"></a>EXTERN (MASM)
定义一个或多个外部变量、 标签或调用的符号*名称*其类型是`type`。  
  
## <a name="syntax"></a>语法  
  
```  
  
   EXTERN [[langtype]] name [[(altid)]] :  
type [[, [[langtype]] name [[(altid)]] :type]]...  
```  
  
## <a name="remarks"></a>备注  
 `type`可以是[ABS](../../assembler/masm/operator-abs.md)，它导入*名称*为常量。 与相同[EXTRN](../../assembler/masm/extrn.md)。  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)