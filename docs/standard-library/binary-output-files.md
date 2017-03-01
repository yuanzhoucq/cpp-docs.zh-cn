---
title: "二进制输出文件 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- I/O [C++], binary output files
- files [C++], binary output files
- binary data, binary output files
ms.assetid: 180954af-8cd6-444b-9a76-2f630a3389d8
caps.latest.revision: 8
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
translationtype: Machine Translation
ms.sourcegitcommit: 85c900f2263ae1c1089478badc85388e3b5e8548
ms.openlocfilehash: f566da8ea00f0a52db3539c81bb3d19d6fc9da99
ms.lasthandoff: 02/24/2017

---
# <a name="binary-output-files"></a>二进制输出文件
流最初专为文本设计，因此默认输出模式为文本。 在文本模式下，换行符（十六进制的 10）扩展为回车换行符（仅 16 位）。 扩展可能会引发如下所示的问题：  
  
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
  
 你可能希望此程序输出字节序列 { 99, 0, 10, 0 }；相反，它输出了 { 99, 0, 13, 10, 0 }，从而导致程序预测二进制输入的问题。 如果需要真正的二进制输出，其中写入的字符未经转译，则可以使用 [ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream__basic_ofstream) 构造函数 openmode 参数指定二进制输出：  
  
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
  
## <a name="see-also"></a>另请参阅  
 [输出流](../standard-library/output-streams.md)


