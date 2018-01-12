---
title: "编译器错误 C2605 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2605
dev_langs: C++
helpviewer_keywords: C2605
ms.assetid: a0e6f132-5acf-4e19-b277-ddf196d182bf
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d7cfd4fefa8cfc28dae3d7431487ed185cf9d2ab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2605"></a>编译器错误 C2605
“name”: 此方法是托管或 WinRT 类中的保留方法  
  
 某些名称由编译器保留用于内部函数。  有关详细信息，请参阅[析构函数和终结器](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。  
  
## <a name="example"></a>示例  
 以下示例生成 C2605。  
  
```  
// C2605.cpp  
// compile with: /clr /c  
ref class R {  
protected:  
   void Finalize() {}   // C2605  
};  
```