---
title: "构造输入流对象 | Microsoft Docs"
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
  - "输入流对象"
ms.assetid: ab94866e-6ffe-4f15-b4db-0bd23e636075
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 构造输入流对象
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您仅使用 `cin` 对象，则无需构造内容。  如果您使用，则必须生成的内容：  
  
-   [输入文件流构造函数](#vclrfinputfilestreamconstructorsanchor8)  
  
-   [输入字符串流构造函数](#vclrfinputstringstreamconstructorsanchor9)  
  
##  <a name="vclrfinputfilestreamconstructorsanchor8"></a> 输入文件流构造函数  
 有两种创建输入文件流：  
  
-   使用 `void` 参数的构造函数，然后调用 `open` 成员函数：  
  
    ```  
    ifstream myFile; // On the stack  
    myFile.open( "filename" );  
  
    ifstream* pmyFile = new ifstream; // On the heap  
    pmyFile->open( "filename" );  
    ```  
  
-   指定文件名模式和标志。构造函数调用，从而打开文件在构造过程中：  
  
    ```  
    ifstream myFile( "filename" );  
    ```  
  
##  <a name="vclrfinputstringstreamconstructorsanchor9"></a> 输入字符串流构造函数  
 输入字符串流构造函数需要预分配的，preinitialized 存储地址：  
  
```  
string s("123.45");  
double amt;  
istringstream myString( s );   
//istringstream myString( "123.45" ) also works  
myString >> amt; // amt contains 123.45  
```  
  
## 请参阅  
 [输入流](../standard-library/input-streams.md)