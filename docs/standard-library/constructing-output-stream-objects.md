---
title: "构造输出流对象 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- output stream objects
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: ca8d4e9a44f4550d02e6d224ce0130d15e81da14
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="constructing-output-stream-objects"></a>构造输出流对象
如果只使用预定义的 `cout`、`cerr` 或 `clog` 对象，则无需构造输出流。 必须为以下对象使用构造函数：  
  
- [输出文件流构造函数](#vclrfoutputfilestreamconstructorsanchor1)  
  
- [输出字符串流构造函数](#vclrfoutputstringstreamconstructorsanchor2)  
  
##  <a name="vclrfoutputfilestreamconstructorsanchor1"></a> 输出文件流构造函数  
 可使用以下两种方式之一构造输出文件流：  
  
-   使用默认的构造函数，然后调用 `open` 成员函数。  
  
 ```  
    ofstream myFile; // Static or on the stack  
    myFile.open("filename");

 
    ofstream* pmyFile = new ofstream; // On the heap  
    pmyFile->open("filename");
```  
  
-   在构造函数调用过程中指定文件名和模式标志。  
  
 ```  
    ofstream myFile("filename", ios_base::out);
```  
  
##  <a name="vclrfoutputstringstreamconstructorsanchor2"></a>输出字符串流构造函数  
 若要构造一个输出字符串流，可以按照以下方法使用 `ostringstream`：  
  
```  
    using namespace std;  
string sp;  
ostringstream myString;  
myString <<"this is a test" <<ends;  
sp = myString.str();
// Obtain string  
cout <<sp <endl;   
```  
  
 `ends`“操控器”向字符串添加必要的终止 null 字符。  
  
## <a name="see-also"></a>另请参阅  
 [输出流](../standard-library/output-streams.md)


