---
title: 托管类型和 main 函数 (C + + /cli CLI) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- main function, in managed applications
- managed code, main() function
ms.assetid: 9d0e9620-58c4-4dac-a0e1-ffeb95f80fa5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6024f4b6e72fa997f816f7fee0b76778c5ebfc4f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="managed-types-and-the-main-function-ccli"></a>托管类型和 main 函数 (C++/CLI)
编写应用程序中使用时 **/clr**的自变量**main （)** 函数不能为托管类型。  
  
 正确签名的一个示例是：  
  
```  
// managed_types_and_main.cpp  
// compile with: /clr  
int main(int, char*[], char*[]) {}  
```  
  
## <a name="see-also"></a>请参阅  
 [托管类型 (C++/CLI)](../dotnet/managed-types-cpp-cli.md)