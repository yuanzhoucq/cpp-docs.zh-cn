---
title: "为自己的类重载 &lt;&lt; 运算符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- operator<<, overloading for your own classes
- operator <<, overloading for your own classes
ms.assetid: ad1d2c49-d84e-48a8-9c09-121f28b10bf0
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d3a1a1ee84cece4babf673acd4858796adc53bc6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="overloading-the-ltlt-operator-for-your-own-classes"></a>为自己的类重载 &lt;&lt; 运算符
输出流使用标准类型的插入 (`<<`) 运算符。 还可以为自己的类重载 `<<` 运算符。  
  
## <a name="example"></a>示例  
 `write` 函数示例演示了 `Date` 结构的使用。 日期是 C++ 类的理想候选，其中数据成员（月、日和年）在视图中处于隐藏状态。 输出流是用于显示这种结构的逻辑目标。 此代码将使用 `cout` 对象显示日期：  
  
```  
Date dt(1, 2, 92);

cout <<dt;  
```  
  
 若要获取 `cout` 以接受插入运算符后的 `Date` 对象，请重载该插入运算符，以识别左侧的 `ostream` 对象和右侧的 `Date`。 然后重载的 `<<` 运算符函数必须作为 `Date` 类的友元进行声明，以便其能够访问 `Date` 对象中的私有数据。  
  
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
  
```Output  
5/6/92  
```  
  
## <a name="remarks"></a>备注  
 重载的运算符将返回原始 `ostream` 对象的引用，这意味着你可以合并插入：  
  
```  
cout <<"The date is" <<dt <<flush;  
```  
  
## <a name="see-also"></a>请参阅  
 [输出流](../standard-library/output-streams.md)

