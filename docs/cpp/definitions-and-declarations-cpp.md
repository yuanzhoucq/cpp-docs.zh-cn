---
title: "定义和声明 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 定义和声明 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 DLL 接口引用已知由此系统中的某个程序导出的所有项（函数和数据）；即，声明为 **dllimport** 或 `dllexport` 的所有项。  DLL 接口中包含的所有声明必须指定 **dllimport** 或 `dllexport` 特性。  但是，该定义仅必须指定 `dllexport` 特性。  例如，以下函数定义产生了一个编译器错误：  
  
```  
__declspec( dllimport ) int func() {   // Error; dllimport  
                                    // prohibited on definition.  
   return 1;  
}  
```  
  
 以下代码也会产生错误：  
  
```  
#define DllImport   __declspec( dllimport )  
  
__declspec( dllimport ) int i = 10;  // Error; this is a  
                                     // definition.  
```  
  
 但是，这是正确的语法：  
  
```  
__declspec( dllexport ) int i = 10;     // Okay--export definition  
```  
  
 使用 `dllexport` 表示定义，而使用 **dllimport** 表示声明。  必须使用带 `dllexport` 的 `extern` 关键字来强制进行声明；否则，会进行隐式定义。  因此，以下示例是正确的：  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
extern DllImport int k; // These are both correct and imply a  
DllImport int j;        // declaration.  
```  
  
 以下示例阐明了前面的示例：  
  
```  
static __declspec( dllimport ) int l; // Error; not declared extern.  
  
void func() {  
    static __declspec( dllimport ) int s;  // Error; not declared  
                                           // extern.  
    __declspec( dllimport ) int m;         // Okay; this is a   
                                           // declaration.  
    __declspec( dllexport ) int n;         // Error; implies external  
                                           // definition in local scope.  
    extern __declspec( dllimport ) int i;  // Okay; this is a  
                                           // declaration.  
    extern __declspec( dllexport ) int k;  // Okay; extern implies  
                                           // declaration.  
    __declspec( dllexport ) int x = 5;     // Error; implies external  
                                           // definition in local scope.  
}  
```  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [dllexport、dllimport](../cpp/dllexport-dllimport.md)