---
title: "输出文件流成员函数 | Microsoft Docs"
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
  - "输出流, 成员函数"
ms.assetid: 38aaf710-8035-4a34-a0c4-123a5327f28a
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 输出文件流成员函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

输出流成员函数有三种类型：操控与等效的代码执行未经授权格式化的写入操作的那些修改，则流状态且没有等效的操控器或运算符插入的那些以及  对于顺序，格式化输出，可能仅使用运算符插入和移动。  对于用于随机访问磁盘二进制输出，则使用其他成员函数，有或没有将运算符插入。  
  
## 输出流打开的函数  
 若要使用输出文件流 \([ofstream](../Topic/ofstream.md)\)，则必须将该流与构造函数或 **打开** 函数的一个特定磁盘文件。  如果使用 **打开** 函数，可以重新使用一系列文件相同的流对象。  在任何情况下，描述文件的参数相同。  
  
 在打开文件与输出流时，通常指定 **open\_mode** 标志。  可以组合这些标志，按位定义为 `ios` 类的枚举器，与或 \(&#124;\) 运算符。  为枚举器的列表参见 [ios\_base::openmode](../Topic/ios_base::openmode.md)。  
  
 以下三种常见情况的输出流涉及模式选项：  
  
-   创建文件。  如果该文件已经存在，会删除旧版本。  
  
    ```  
    ostream ofile( "FILENAME" );  // Default is ios::out  
    ofstream ofile( "FILENAME", ios::out ); // Equivalent to above  
    ```  
  
-   将日志追加到现有文件或创建一个，如果它不存在。  
  
    ```  
    ofstream ofile( "FILENAME", ios::app );  
    ```  
  
-   打开两个文件中，一次一个，在相同流。  
  
    ```  
    ofstream ofile();  
    ofile.open( "FILE1", ios::in );  
    // Do some output  
    ofile.close(); // FILE1 closed  
    ofile.open( "FILE2", ios::in );  
    // Do some more output  
    ofile.close(); // FILE2 closed  
    // When ofile goes out of scope it is destroyed.  
    ```  
  
## 放置的函数  
 **put** 函数编写字符到输出流。  以下两个语句相同的默认方式，但第二个受流的格式参数的影响：  
  
```  
cout.put( 'A' ); // Exactly one character written  
cout << 'A'; // Format arguments 'width' and 'fill' apply   
```  
  
## 编写函数  
 **write** 函数写入内存块为输出文件流。  长度参数指定编写的字节数。  此示例为创建输出文件流和写入 `Date` 配置的二进制值。它：  
  
```  
// write_function.cpp  
// compile with: /EHsc  
#include <fstream>  
using namespace std;  
  
struct Date  
{  
   int mo, da, yr;  
};  
  
int main( )  
{  
   Date dt = { 6, 10, 92 };  
   ofstream tfile( "date.dat" , ios::binary );  
   tfile.write( (char *) &dt, sizeof dt );  
}  
```  
  
 **write** 函数不停止，当到达空字符，因此，整个一结构层编写。  函数采用两个参数：`char` 指针和写入的计数字符。  请注意所需转换为 **char\***，在结构对象的地址。  
  
## seekp 和 tellp 函数  
 输出文件流指向位置保留数据将写入接下来的内部指针。  `seekp` 成员函数将此指针和行为提供随机访问磁盘文件输出。  `tellp` 成员函数返回文件位置。  有关使用内容等效于 `seekp` 和 `tellp`的示例，请参见 [seekg 和 tellg 函数](../standard-library/input-stream-member-functions.md)。  
  
## 输出流中接近的函数  
 **关闭** 成员函数关闭磁盘文件与输出文件流。  必须关闭文件完成所有磁盘输出。  如有必要，`ofstream` 析构函数中关闭您的文件，但是，您可以使用 **关闭** 函数是否需要打开相同的流对象的其他文件。  
  
 在构造函数或 **打开** 成员函数。文件，打开输出流析构函数会自动关闭流的文件。  如果您经过构造函数已打开文件的文件说明符使用或 **附加** 成员函数，则必须显式关闭文件。  
  
##  <a name="vclrferrorprocessingfunctionsanchor10"></a> 处理函数的错误  
 请使用这些成员函数测试错误，在写入流时：  
  
|功能|返回值|  
|--------|---------|  
|[错误](../Topic/basic_ios::bad.md)|如果一个具有不可恢复的错误，将返回 **true**。|  
|[失败](../Topic/basic_ios::fail.md)|返回 **true**，如果一个具有不可恢复的错误或一“预期的条件”，例如转换错误，或者，如果未找到该文件。  处理在调用后继续。通常为零的参数的 **清除**。|  
|[好](../Topic/basic_ios::good.md)|返回 **true**，如果没有错误状态 \(不可恢复或\)，并且文件尾未设置任何标志。|  
|[eof](../Topic/basic_ios::eof.md)|返回在该文件的条件的 **true**。|  
|[clear](../Topic/basic_ios::clear.md)|为内部错误状态。  如果调用具有默认参数，就会清除所有错误位。|  
|[rdstate](../Topic/basic_ios::rdstate.md)|返回当前错误状态。|  
  
 \#\#\#\!运算符重载执行函数和 **失败** 函数相同。  因此表达式：  
  
```  
if( !cout)...  
```  
  
 等效于：  
  
```  
if( cout.fail() )...  
```  
  
 **void\*\(\)** 运算符是重载 \#\#\#\!运算符的相反；因此表达式：  
  
```  
if( cout)...  
```  
  
 等于于：  
  
```  
if( !cout.fail() )...  
```  
  
 因为它不测试文件尾，**void\*\(\)** 运算符与 **good** 将不再等效的。  
  
## 请参阅  
 [输出流](../standard-library/output-streams.md)