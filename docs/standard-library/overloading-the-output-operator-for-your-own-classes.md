---
title: "为您自己的类重载 &lt;&lt; 运算符 | Microsoft Docs"
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
  - "运算符 <<, 针对您自己的类进行重载"
  - "operator<<, 针对您自己的类进行重载"
ms.assetid: ad1d2c49-d84e-48a8-9c09-121f28b10bf0
caps.latest.revision: 12
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 为您自己的类重载 &lt;&lt; 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

输出流为使用标准类型插入 \(`<<`\) 运算符。  还可以自己的运算符重载的 `<<` 类。  
  
## 示例  
 `write` 函数的示例演示了使用 `Date` 结构。  日期是数据成员的 C.C\+\+ 类的一个 \(的理想候选月、日和年\) 是隐藏的。  输出流是显示的此结构逻辑目标。  使用 `cout` 对象，代码显示日期：  
  
```  
Date dt( 1, 2, 92 );  
cout << dt;  
```  
  
 若要获取 `cout`。将运算符插入后也接受 `Date` 对象，则重载运算符插入识别左侧的 `ostream` 对象和右侧的 `Date`。  必须再声明运算符重载的 `<<` 函数中，类 `Date`，因此可以在 `Date` 内的友元访问对象的私有数据。  
  
```  
// overload_date.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
class Date  
{  
    int mo, da, yr;  
public:  
    Date(int m, int d, int y)  
    {  
        mo = m; da = d; yr = y;  
    }  
    friend ostream& operator<<(ostream& os, const Date& dt);  
};  
  
ostream& operator<<(ostream& os, const Date& dt)  
{  
    os << dt.mo << '/' << dt.da << '/' << dt.yr;  
    return os;  
}  
  
int main()  
{  
    Date dt(5, 6, 92);  
    cout << dt;  
}  
```  
  
  **5\/6\/92**   
## 备注  
 重载运算符返回到原始 `ostream` 对象的引用，这意味着可以将插入：  
  
```  
cout << "The date is" << dt << flush;  
```  
  
## 请参阅  
 [输出流](../standard-library/output-streams.md)