---
title: "fp_contract | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.fp_contract"
  - "fp_contract_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "fp_contract 杂注"
  - "杂注, fp_contract"
ms.assetid: 15b97338-6680-4287-ba2a-2dccc5b2ccf5
caps.latest.revision: 12
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fp_contract
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

确定浮点缩写式是否将发生。  
  
## 语法  
  
```  
#pragma fp_contract [ON | OFF]  
```  
  
## 备注  
 默认情况下，`fp_contract` 处于打开状态。  
  
 有关浮点行为的详细信息，请参阅 [\/fp（指定浮点行为）](../build/reference/fp-specify-floating-point-behavior.md)。  
  
 其他浮点杂注包括：  
  
-   [fenv\_access](../preprocessor/fenv-access.md)  
  
-   [float\_control](../preprocessor/float-control.md)  
  
## 示例  
 从该示例中生成的代码不使用 Itanium 处理器上的 Fused Multiply Add \(**fma**\) 指令。  如果注释掉 `#pragma fp_contract (off)`，则生成的代码将使用 **fma** 指令。  
  
```  
// pragma_directive_fp_contract.cpp  
// compile with: /O2  
#include <stdio.h>  
#include <float.h>  
  
#pragma fp_contract (off)   
  
int main() {  
   double z, b, t;  
  
   for (int i = 0; i < 10; i++) {  
      b = i * 5.5;  
      t = i * 56.025;  
      _set_controlfp(_PC_24, _MCW_PC);  
  
      z = t * i + b;  
      printf_s ("out=%.15e\n", z);  
   }  
}  
```  
  
  **out\=0.000000000000000e\+000**  
**out\=6.152500152587891e\+001**  
**out\=2.351000061035156e\+002**  
**out\=5.207249755859375e\+002**  
**out\=9.184000244140625e\+002**  
**out\=1.428125000000000e\+003**  
**out\=2.049899902343750e\+003**  
**out\=2.783724853515625e\+003**  
**out\=3.629600097656250e\+003**  
**out\=4.587524902343750e\+003**   
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)