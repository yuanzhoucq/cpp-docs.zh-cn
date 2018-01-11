---
title: "#<a name=\"error-directive-cc--microsoft-docs\"></a>错误指令 （C/c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '#error'
dev_langs: C++
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a14786834843046fc1e6cf551eaf95d1b28a8624
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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