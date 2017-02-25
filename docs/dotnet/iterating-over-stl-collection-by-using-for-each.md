---
title: "使用 for each 循环访问 STL 集合 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DTL 集合, 循环访问"
ms.assetid: 9358ca29-b982-4a19-bbfd-bef50fe66c9a
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# 使用 for each 循环访问 STL 集合
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`for each` 关键字可用于循环访问标准 C\+\+ 库 \(STL 集合\)。  
  
## 所有平台  
 **备注**  
  
 也称为 STL 集合是 *容器*。  有关详细信息，请参阅[STL 容器](../standard-library/stl-containers.md)。  
  
## 示例  
 **示例**  
  
 下面的代码示例使用 `for each` 循环访问 [\< 映射 \>](../standard-library/map.md)。  
  
```  
// for_each_stl.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
#include <string>  
using namespace std;  
  
int main() {  
   int retval  = 0;  
   map<string, int> months;  
  
   months["january"] = 31;  
   months["february"] = 28;  
   months["march"] = 31;  
   months["april"] = 30;  
   months["may"] = 31;  
   months["june"] = 30;  
   months["july"] = 31;  
   months["august"] = 31;  
   months["september"] = 30;  
   months["october"] = 31;  
   months["november"] = 30;  
   months["december"] = 31;  
  
   map<string, int> months_30;  
  
   for each( pair<string, int> c in months )  
      if ( c.second == 30 )  
         months_30[c.first] = c.second;  
  
   for each( pair<string, int> c in months_30 )  
      retval++;  
  
   cout << "Months with 30 days = " << retval << endl;  
}  
```  
  
 **Output**  
  
  **使用 30 天的月份 \= 4** **示例**  
  
 下面的代码示例用于 STL 容器中的迭代变量使用常数引用 \(`const&`\)。  可以使用引用 \(`&`\) 声明为可以为 *T*类型`&`的任何集合的迭代变量。  
  
```  
// for_each_stl_2.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
using namespace std;  
  
int main() {  
   int retval = 0;  
  
   vector<int> col(3);  
   col[0] = 10;  
   col[1] = 20;  
   col[2] = 30;  
  
   for each( const int& c in col )  
      retval += c;  
  
   cout << "retval: " << retval << endl;  
}  
```  
  
 **Output**  
  
  **retval: 60**   
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **备注**  
  
 （此功能没有特定于平台的备注。）  
  
### 要求  
 编译器选项：**\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **备注**  
  
 （此功能没有特定于平台的备注。）  
  
### 要求  
 编译器选项：**\/clr**  
  
## 请参阅  
 [for each，in](../dotnet/for-each-in.md)   
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)