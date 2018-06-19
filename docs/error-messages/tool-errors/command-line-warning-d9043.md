---
title: 命令行警告 D9043 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9043
dev_langs:
- C++
helpviewer_keywords:
- D9043
ms.assetid: 9263e28d-217b-414c-bfb6-86efd3c27a77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65bf672418b49dbf6017374ab7cd18caa61d7403
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294744"
---
# <a name="command-line-warning-d9043"></a>命令行警告 D9043
无效的值为 compiler_option; 后面的 warning_level假设 '4999';代码分析警告不与警告级别相关联  
  
## <a name="example"></a>示例  
 下面的示例生成 C9043。  
  
```  
// D9043.cpp  
// compile with: /analyze /w16001  
// D9043 warning expected  
int main() {}  
```