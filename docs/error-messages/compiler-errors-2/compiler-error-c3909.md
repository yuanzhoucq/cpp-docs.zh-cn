---
title: "编译器错误 C3909 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3909
dev_langs: C++
helpviewer_keywords: C3909
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5cb5929fe1619ce75a7bde15ac08955247f1af7a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3909"></a>编译器错误 C3909
aWinRT 或托管的事件声明必须出现在 WinRT 或托管的类型  
  
 Windows 运行时事件或托管事件是在本机类型中声明的。 要修复此错误，请在 Windows 运行时类型或托管类型中声明事件。  
  
 有关详细信息，请参阅[事件](../../windows/event-cpp-component-extensions.md)。  
  
 下面的示例生成 C3909，并演示如何修复此错误：  
  
```  
// C3909.cpp  
// compile with: /clr /c  
delegate void H();  
class X {  
   event H^ E;   // C3909 - use ref class X instead  
};  
  
ref class Y {  
   static event H^ E {  
      void add(H^) {}  
      void remove( H^ h ) {}  
      void raise( ) {}  
   }  
};  
```