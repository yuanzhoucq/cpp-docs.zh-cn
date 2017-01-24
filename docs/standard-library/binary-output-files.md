---
title: "二进制输出文件 | Microsoft Docs"
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
  - "二进制数据, 二进制输出文件"
  - "文件 [C++], 二进制输出文件"
  - "I/O [C++], 二进制输出文件"
ms.assetid: 180954af-8cd6-444b-9a76-2f630a3389d8
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 二进制输出文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

流为文本最初设计，因此，默认输出方法是文本。  在文本模式字符，换行 \(十六进制为 16 位 10\) 展开支架的返回换行符 \(仅\)。  扩展会造成问题，如下所示：  
  
```  
// binary_output_files.cpp  
// compile with: /EHsc  
#include <fstream>  
using namespace std;  
int iarray[2] = { 99, 10 };  
int main( )  
{  
    ofstream os( "test.dat" );  
    os.write( (char *) iarray, sizeof( iarray ) );  
}  
```  
  
 可能希望该程序输出字节序列{99，0，10，0};相反，它输出{99，0，13，10，0}，生成是二进制的输入程序中的问题。  如果需要的二进制输出，可以使用 [ofstream](../Topic/ofstream.md) 构造函数模式参数，将字符写入尚未，可以指定该二进制输出：  
  
```  
// binary_output_files2.cpp  
// compile with: /EHsc  
#include <fstream>  
using namespace std;  
int iarray[2] = { 99, 10 };  
  
int main()  
{  
   ofstream ofs ( "test.dat", ios_base::binary );  
  
   // Exactly 8 bytes written  
   ofs.write( (char*)&iarray[0], sizeof(int)*2 );   
}  
```  
  
## 请参阅  
 [输出流](../standard-library/output-streams.md)