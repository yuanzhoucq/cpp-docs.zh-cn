---
title: "编译和链接多线程程序 | Microsoft Docs"
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
  - "编译多线程程序"
  - "编译源代码 [C++], 多线程程序"
  - "链接 [C++], 多线程程序"
  - "多线程处理 [C++], 编译的程序"
  - "多线程处理 [C++], 链接程序"
  - "线程处理 [C++], 编译的程序"
  - "线程处理 [C++], 链接程序"
ms.assetid: 27589afc-daf2-4f26-b868-a99de5c9dfec
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译和链接多线程程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在[多线程 C 程序示例](../parallel/sample-multithread-c-program.md)中对 Bounce.c 程序进行了介绍。  
  
 默认情况下，程序以多线程形式进行编译。  
  
#### 从开发环境内编译和链接多线程程序 Bounce.c  
  
1.  在**“文件”**菜单上单击**“新建”**，再单击**“项目”**。  
  
2.  在**“项目类型”**窗格中，单击**“Win32”**。  
  
3.  在**“模板”**窗格中，单击**“Win32 控制台应用程序”**，然后命名项目。  
  
4.  将包含 C 源代码的文件添加到项目中。  
  
5.  在**“生成”**菜单上，通过单击**“生成”**命令生成项目。  
  
#### 从命令行编译和链接多线程程序 Bounce.c  
  
1.  编译和链接程序：  
  
    ```  
    CL BOUNCE.C  
    ```  
  
## 请参阅  
 [使用 C 和 Win32 进行多线程编程](../parallel/multithreading-with-c-and-win32.md)