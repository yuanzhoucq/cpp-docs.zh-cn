---
title: "使用 for each 循环访问 c + + 标准库集合 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords: DTL collections, iterating over
ms.assetid: 9358ca29-b982-4a19-bbfd-bef50fe66c9a
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1a4ce2de13380895f1f313559abeb87e4cd65db2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="iterating-over-c-standard-library-collection-by-using-for-each"></a>使用 for each 循环访问 c + + 标准库集合
`for each`关键字可用于循环访问 c + + 标准库集合。  
  
## <a name="all-platforms"></a>所有平台  
 **备注**  
  
 C + + 标准库集合是也称为*容器*。 有关详细信息，请参阅 [C++ 标准库容器](../standard-library/stl-containers.md)。  
  
## <a name="examples"></a>示例  
 **示例**  
  
 下面的代码示例使用`for each`要循环访问[\<映射 >](../standard-library/map.md)。  
  
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
  
 **输出**  
  
```Output  
Months with 30 days = 4  
```  
  
 **示例**  
  
 下面的代码示例使用的常量引用 (`const&`) 于与 c + + 标准库容器的迭代变量。 你可以使用的引用 (`&`) 上可以声明为任何的类型集合的迭代变量作为*T*`&`。  
  
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
  
 **输出**  
  
```Output  
retval: 60  
```  
  
## <a name="windows-runtime"></a>Windows 运行时  
 **备注**  
  
 有关于此功能没有特定于平台的备注。  
  
### <a name="requirements"></a>惠?  
 编译器选项： **/ZW**  
  
## <a name="common-language-runtime"></a>公共语言运行时 
 **备注**  
  
 有关于此功能没有特定于平台的备注。  
  
### <a name="requirements"></a>惠?  
 编译器选项： **/clr**  
  
## <a name="see-also"></a>请参阅  
 [对于每一个，在](../dotnet/for-each-in.md)   
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)