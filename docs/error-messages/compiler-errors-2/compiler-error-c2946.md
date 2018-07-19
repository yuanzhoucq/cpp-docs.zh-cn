---
title: 编译器错误 C2946 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2946
dev_langs:
- C++
helpviewer_keywords:
- C2946
ms.assetid: c86dfbfc-7702-4f09-8a53-d205710e99c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9485f424306d66514c9e919f13ff5988f8b0d1f2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33247066"
---
# <a name="compiler-error-c2946"></a>编译器错误 C2946
显式实例化；“类”不是模板类专用化  
  
 不能显式实例化非模板化的类。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2946。  
  
```  
// C2946.cpp  
class C {};  
template C;  // C2946  
int main() {}  
```