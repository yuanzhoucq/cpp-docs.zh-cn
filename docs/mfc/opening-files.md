---
title: "打开文件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFile 类, 变量"
  - "示例 [MFC], 打开文件"
  - "异常处理 [C++], 打开文件"
  - "异常处理 [C++], 打开文件时"
  - "文件对象 [C++]"
  - "文件 [C++], 打开"
  - "MFC [C++], 文件操作"
  - "打开调用"
  - "打开成员函数"
  - "Open 方法, CFile 类"
  - "打开文件"
  - "打开文件, 处理异常"
  - "打开文件, 在 MFC 中"
ms.assetid: a991b8ec-b04a-4766-b47e-7485b5dd0b01
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 打开文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 MFC 中，最常见的情况下打开文件这一过程包含两个阶段。  
  
#### 用于打开文件。  
  
1.  创建对象文件，无需指定路径或权限标志。  
  
     通过声明在堆栈帧中的 [CFile](../mfc/reference/cfile-class.md) 变量通常创建文件对象。  
  
2.  调用文件对象的函数 [打开](../Topic/CFile::Open.md) 成员，并提供路径和权限的标志。  
  
     `Open` 的返回值是非零，如果成功打开的文件或 0，则无法打开所指定的文件。  原型非 `Open` 成员函数如下所示：  
  
     `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`  
  
     打开标志指定哪些权限，如是只读的，则为文件需要。  可能的标志值定义为在 `CFile` 类中枚举的常数，因此，其限定使用“`CFile::`”`CFile::modeRead`。  如果需要创建文件，请使用 `CFile::modeCreate`。  
  
 下面的示例演示如何创建具有读\/写权限的新文件 \(替换任何以前的文件的同一路径\):  
  
 [!code-cpp[NVC_MFCFiles#1](../mfc/codesnippet/CPP/opening-files_1.cpp)]  
  
> [!NOTE]
>  此示例创建并打开文件。  如果存在问题，`Open` 调用中返回在其最后参数的 `CFileException` 对象，如下所示。  `TRACE` 宏打印文件名和代码指示失败的原因。  可以调用 `AfxThrowFileException` 函数是否需要更加详细的错误报告。  
  
## 请参阅  
 [CFile Class](../mfc/reference/cfile-class.md)   
 [CFile::Open](../Topic/CFile::Open.md)   
 [文件](../mfc/files-in-mfc.md)