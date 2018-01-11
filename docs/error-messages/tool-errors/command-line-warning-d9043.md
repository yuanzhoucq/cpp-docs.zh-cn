---
title: "命令行警告 D9043 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: D9043
dev_langs: C++
helpviewer_keywords: D9043
ms.assetid: 9263e28d-217b-414c-bfb6-86efd3c27a77
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a8986926db2c32d9ae5ca73517c74ae9625e6bf5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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