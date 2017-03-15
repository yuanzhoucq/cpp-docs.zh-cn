---
title: "指定路径名 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 编译器, 输出文件"
  - "名称 [C++], 编译器输出文件"
  - "输出文件, 指定路径名"
ms.assetid: 7a6595ce-3383-44ae-957a-466bfa29c343
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 指定路径名
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

每个输出文件选项接受一个 *pathname* 参数，该参数可以指定输出文件的位置和名称。  此参数可以包括驱动器名、目录和文件名。  选项和参数之间不允许有空格。  
  
 如果 *pathname* 包括没有扩展名的文件名，编译器将为输出提供默认扩展名。  如果 *pathname* 包括目录却没有文件名，编译器将在指定目录中创建具有默认名称的文件。  默认名称基于源文件的基名称和基于输出文件类型的默认扩展名。  如果完全不使用 *pathname*，编译器将在默认目录中创建具有默认名称的文件。  
  
 *pathname* 参数也可以是设备名（AUX、CON、PRN 或 NUL）而不是文件名。  不要在选项和设备名之间使用空格或将冒号用作设备名的一部分。  
  
|设备名|表示|  
|---------|--------|  
|AUX|辅助设备|  
|CON|控制台|  
|PRN|打印机|  
|NUL|空设备（不创建任何文件）|  
  
## 示例  
 下列命令行将映射文件发送到打印机：  
  
```  
CL /FmPRN HELLO.CPP  
```  
  
## 请参阅  
 [输出文件 \(\/F\) 选项](../../build/reference/output-file-f-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)