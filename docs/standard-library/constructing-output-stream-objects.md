---
title: "构造输出流对象 | Microsoft Docs"
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
  - "输出流对象"
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
caps.latest.revision: 9
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 构造输出流对象
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果使用预定义的 `cout`、`cerr`或 `clog` 对象，只不需要构造输出流。  必须使用构造函数：  
  
-   [输出文件流构造函数](#vclrfoutputfilestreamconstructorsanchor1)  
  
-   [输出字符串流构造函数](#vclrfoutputstringstreamconstructorsanchor2)  
  
##  <a name="vclrfoutputfilestreamconstructorsanchor1"></a> 输出文件流构造函数  
 可以用下列两种方法之一来构造一输出文件流：  
  
-   使用默认构造函数，然后调用 `open` 成员函数。  
  
    ```  
    ofstream myFile; // Static or on the stack  
    myFile.open( "filename" );  
  
    ofstream* pmyFile = new ofstream; // On the heap  
    pmyFile->open( "filename" );  
    ```  
  
-   指定文件名模式和标志。构造函数调用。  
  
    ```  
    ofstream myFile( "filename", ios_base::out);  
    ```  
  
##  <a name="vclrfoutputstringstreamconstructorsanchor2"></a> 输出字符串流构造函数  
 若要构造字符串输出流，则可以采用以下方式使用 `ostringstream` :  
  
```  
   using namespace std;  
string sp;  
ostringstream myString;  
myString << "this is a test" << ends;  
sp = myString.str();  // Obtain string  
cout << sp < endl;   
```  
  
 操控”`ends`“将必要的终止 null 字符为字符串。  
  
## 请参阅  
 [输出流](../standard-library/output-streams.md)