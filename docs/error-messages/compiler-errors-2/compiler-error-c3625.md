---
title: "编译器错误 C3625 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3625
dev_langs:
- C++
helpviewer_keywords:
- C3625
ms.assetid: fdf49f21-d6b1-42f4-9eec-23b04ae8b4aa
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: c49600c823965dc92e0decab3048f076169d43fe
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3625"></a>编译器错误 C3625
“native_type”：本机类型不能从托管或 WinRT 类型“type”派生  
  
本机类不能从托管或 WinRT 类继承。 有关详细信息，请参阅[类和结构](../../windows/classes-and-structs-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
以下示例生成 C3625：  
  
```  
// C3625.cpp  
// compile with: /clr /c  
ref class B {};  
class D : public B {};   // C3625 cannot inherit from a managed class  
```  

