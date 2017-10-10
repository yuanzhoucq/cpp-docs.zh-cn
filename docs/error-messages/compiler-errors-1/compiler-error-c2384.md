---
title: "编译器错误 C2384 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2384
dev_langs:
- C++
helpviewer_keywords:
- C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 0d87769a2e02e6214e474dab2b74859e85a6880b
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2384"></a>编译器错误 C2384
“membe”：不能对托管类或 WinRT 类的成员应用 __declspec(thread)  
  
 [线程](../../cpp/thread.md)`__declspec`修饰符不能使用上托管的成员或 Windows 运行时类。  
  
 托管代码中的静态线程本地存储仅可用于静态加载的 DLL（进程启动时，必须以静态方式加载该 DLL）。 Windows 运行时不支持线程本地存储。  
  
 下面的行生成 C2384 并演示如何在 C++/CLI 代码中修复此错误：  
  
```  
// C2384.cpp  
// compile with: /clr /c  
public ref class B {  
public:  
   __declspec( thread ) static int tls_i = 1;   // C2384  
  
   // OK - declare with attribute instead  
   [System::ThreadStaticAttribute]  
   static int tls_j;  
};  
```
