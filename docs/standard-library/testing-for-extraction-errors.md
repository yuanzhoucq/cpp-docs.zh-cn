---
title: "测试是否出现提取错误 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: extraction errors
ms.assetid: 6a681028-adba-4557-8f7b-f137932905f8
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0dc8c053181eda8535eb101352e9aa50053a28f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="testing-for-extraction-errors"></a>测试提取错误
处理函数时出现的输出错误适用于输入流，请参阅[处理函数时出错](../standard-library/output-file-stream-member-functions.md)。 在提取过程测试是否有错误非常重要。 请看下面的语句：  
  
```  
cin>> n;  
```  
  
 如果 `n` 是一个带符号整数且使用大于 32,767 的值（最大允许值或 MAX_INT）设置流的 `fail` 位，则 `cin` 对象将不可用。 所有后续提取都会立即返回，不会存储任何值。  
  
## <a name="see-also"></a>请参阅  
 [输入流](../standard-library/input-streams.md)

