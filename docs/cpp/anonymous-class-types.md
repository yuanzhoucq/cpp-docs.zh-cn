---
title: "匿名类类型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- class types [C++], anonymous
- anonymous class types
ms.assetid: 9ba667b2-8c2a-4c29-82a6-fa120b9233c8
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 29313d499f7459175c9dc2331148cdd6401e5e53
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="anonymous-class-types"></a>匿名类类型
类可以是匿名 — 也就是说，它们可以声明而无需*标识符*。 在将类名称替换为 `typedef` 名称时，这会很有用，如下所示：  
  
```  
typedef struct  
{  
    unsigned x;  
    unsigned y;  
} POINT;  
```  
  
> [!NOTE]
>  上面示例中显示的匿名类的用法对于保留与现有 C 代码的兼容性很有用。 在某些 C 代码中，将 `typedef` 与匿名结构结合使用是很普遍的。  
  
 如果您希望对类成员的引用就像它未包含在独立类中的情况一样出现，则匿名类也很有用，如下所示：  
  
```  
struct PTValue  
{  
    POINT ptLoc;  
    union  
    {  
        int  iValue;  
        long lValue;  
    };  
};  
  
PTValue ptv;  
```  
  
 在前面的代码中，`iValue`可以使用对象成员选择运算符访问 (**。**)，如下所示：  
  
```  
int i = ptv.iValue;  
```  
  
 匿名类受某些限制的约束。 (有关匿名联合的详细信息，请参阅[联合](../cpp/unions.md)。)匿名类：  
  
-   不能具有构造函数或析构函数。  
  
-   不能作为函数的参数传递（除非使用省略号使类型检查无效）。  
  
-   无法作为函数中的返回值返回。  
  
## <a name="anonymous-structs"></a>匿名结构  
  
### <a name="microsoft-specific"></a>Microsoft 专用  
 利用 Microsoft C 扩展，您可以在另一个结构中声明结构变量，而无需为其指定名称。 这些嵌套结构称为匿名结构。 C++ 不允许匿名结构。  
  
 您可以像访问包含结构中的成员一样访问匿名结构的成员。  
  
```  
// anonymous_structures.c  
#include <stdio.h>  
  
struct phone  
{  
    int  areacode;  
    long number;  
};  
  
struct person  
{  
    char   name[30];  
    char   gender;  
    int    age;  
    int    weight;  
    struct phone;    // Anonymous structure; no name needed  
} Jim;  
  
int main()  
{  
    Jim.number = 1234567;  
    printf_s("%d\n", Jim.number);     
}  
//Output: 1234567  
```  
  
**结束 Microsoft 专用**  
  

