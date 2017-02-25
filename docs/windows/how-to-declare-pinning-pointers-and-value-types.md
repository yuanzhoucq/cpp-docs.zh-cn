---
title: "如何：声明钉住指针和值类型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "钉住指针"
  - "值类型, 声明"
ms.assetid: 57c5ec8a-f85a-48c4-ba8b-a81268bcede0
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 如何：声明钉住指针和值类型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

只有值类型可以装箱。  然后可以声明钉住的指针到装箱值类型的值类型对象和使用 **pin\_ptr**。  
  
## 示例  
  
### 代码  
  
```  
// pin_ptr_value.cpp  
// compile with: /clr  
value struct V {  
   int i;  
};  
  
int main() {  
   V ^ v = gcnew V;   // imnplicit boxing  
   v->i=8;  
   System::Console::WriteLine(v->i);  
   pin_ptr<V> mv = &*v;  
   mv->i = 7;  
   System::Console::WriteLine(v->i);  
   System::Console::WriteLine(mv->i);  
}  
```  
  
### Output  
  
```  
8  
7  
7  
```  
  
## 请参阅  
 [pin\_ptr \(C\+\+\/CLI\)](../windows/pin-ptr-cpp-cli.md)