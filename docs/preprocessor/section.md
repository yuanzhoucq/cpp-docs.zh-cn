---
title: "节 | Microsoft Docs"
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
  - "section_CPP"
  - "vc-pragma.section"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "杂注, 节"
  - "节杂注"
ms.assetid: c67215e9-2c4a-4b0f-b691-2414d2e2d96f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 节
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 .obj 文件中创建一个节。  
  
## 语法  
  
```  
  
#pragma section( "section-name" [, attributes] )  
```  
  
## 备注  
 本主题中的术语“段”和“节”的含义是可互换的。  
  
 一旦节被定义，它将对编译的其余部分保持有效。  但是，您必须使用 [\_\_declspec\(allocate\)](../cpp/allocate.md)，否则不会将任何内容放入该节中。  
  
 *section\-name* 是一个必需参数，它将是该节的名称。  该名称不得与任何标准节名称发生冲突。  有关在创建部分时不应使用的名称的列表，请参阅 [\/SECTION](../build/reference/section-specify-section-attributes.md)。  
  
 `attributes` 是一个可选参数，包括要分配给该节的一个或多个逗号分隔的特性。  可能的 `attributes` 为：  
  
 **read**  
 允许对数据进行读取操作。  
  
 **write**  
 允许对数据进行写入操作。  
  
 **execute**  
 允许执行代码。  
  
 **共享**  
 在所有加载图像的进程之间共享该节。  
  
 **nopage**  
 将该节标记为不可分页：对于 Win32 设备驱动程序很有用。  
  
 **nocache**  
 将该节标记为不可缓存：对于 Win32 设备驱动程序很有用。  
  
 **discard**  
 将该节标记为可丢弃；对于 Win32 设备驱动程序很有用。  
  
 **remove**  
 将该节标记为非内存驻留；仅虚拟设备驱动程序 \(V*x*D\)。  
  
 如果不指定特性，则该节将具有读写特性。  
  
## 示例  
 在下面的示例中，第一个指令标识节及其特性。  不会将整数 `j` 放置到 `mysec` 中，因为它不是使用 `__declspec(allocate)` 声明的；`j` 将进入数据节。  整数 `i` 将进入 `mysec` 作为其 `__declspec(allocate)` 存储类特性的结果。  
  
```  
// pragma_section.cpp  
#pragma section("mysec",read,write)  
int j = 0;  
  
__declspec(allocate("mysec"))  
int i = 0;  
  
int main(){}  
```  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)