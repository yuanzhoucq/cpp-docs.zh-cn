---
title: '#错误指令 （C/c + +） |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#error'
dev_langs:
- C++
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba4f0e06798bc6419f8db0471f19588039eb679a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33905567"
---
# <a name="error-directive-cc"></a>#error 指令 (C/C++)
`#error`指令在编译时发出用户指定的错误消息，然后终止编译。  
  
## <a name="syntax"></a>语法  
  
```  
#errortoken-string  
```  
  
## <a name="remarks"></a>备注  
 此指令发出的错误消息包括*令牌字符串*参数。 `token-string`参数不是受宏展开的约束。 此指令通知程序不一致的开发人员或违反了约束在预处理期间将最为有用。 下面的示例演示了在预处理期间处理的错误：  
  
```  
#if !defined(__cplusplus)  
#error C++ compiler required.  
#endif  
```  
  
## <a name="see-also"></a>请参阅  
 [预处理器指令](../preprocessor/preprocessor-directives.md)