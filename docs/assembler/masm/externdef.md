---
title: "EXTERNDEF |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EXTERNDEF
dev_langs: C++
helpviewer_keywords: EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a06378b7cf1217c01f57d7994220bfe5dd585a66
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="externdef"></a>EXTERNDEF
定义一个或多个外部变量、 标签或调用的符号*名称*其类型是`type`。  
  
## <a name="syntax"></a>语法  
  
```  
  
EXTERNDEF [[langtype]] name:type [[, [[langtype]] name:type]]...  
```  
  
## <a name="remarks"></a>备注  
 如果*名称*定义在模块中，它将被视为[公共](../../assembler/masm/public-masm.md)。 如果*名称*引用在模块中，它将被视为[EXTERN](../../assembler/masm/extern-masm.md)。 如果*名称*是它未被引用，将被忽略。 `type`可以是[ABS](../../assembler/masm/operator-abs.md)，它导入*名称*为常量。 通常情况下用于在包括文件。  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)