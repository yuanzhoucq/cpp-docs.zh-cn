---
title: "C + + 位字段 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- bitfields [C++]
- fields [C++], bit
- bit fields
ms.assetid: 6f4b62e3-cc1d-4e5d-bf34-05904104f71a
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 71f70995cf1a59153a380f0e22f0321fd59abee0
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="c-bit-fields"></a>C++ 位域
类和结构可包含比整型类型占用更少存储空间的成员。 这些成员被指定为位域。 位域的语法*成员声明符*规范如下所示：  
  
## <a name="syntax"></a>语法  
  
```  
  
declarator  : constant-expression  
```  
  
## <a name="remarks"></a>备注  
 （可选）`declarator` 是在程序中访问成员的名称。 它必须是整型类型（包括枚举类型）。 *常量表达式*结构中指定的成员所占据的位数。 匿名位域 — 即不带标识符的位域成员，可用于填充。  
  
> [!NOTE]
>  宽度为 0 的未命名位域强制将下一个位域与下一个 `type` 边界对齐，其中 `type` 是成员的类型。  
  
 下面的示例声明包含位域的结构：  
  
```  
// bit_fields1.cpp  
// compile with: /LD  
struct Date {  
   unsigned short nWeekDay  : 3;    // 0..7   (3 bits)  
   unsigned short nMonthDay : 6;    // 0..31  (6 bits)  
   unsigned short nMonth    : 5;    // 0..12  (5 bits)  
   unsigned short nYear     : 8;    // 0..100 (8 bits)  
};  
```  
  
 `Date` 类型的对象的概念上的内存布局如下图所示。  
  
 ![Date 对象的内存布局](../cpp/media/vc38uq1.png "vc38UQ1")  
数据对象的内容布局  
  
 请注意，`nYear`长度为 8 位，并且会溢出声明的类型的字边界**无符号短**。 因此，它始于的一个新的开头**无符号短**。 并不必使所有位域均适合基础类型的对象；根据声明中请求的位数来分配新的存储单元。  
  
 **Microsoft 专用**  
  
 声明为位域的数据从低位到高位进行排序，如上图所示。  
  
 **结束 Microsoft 专用**  
  
 如果结构的声明包含长度为 0 的未命名字段（如以下示例所示），  
  
```  
// bit_fields2.cpp  
// compile with: /LD  
struct Date {  
   unsigned nWeekDay  : 3;    // 0..7   (3 bits)  
   unsigned nMonthDay : 6;    // 0..31  (6 bits)  
   unsigned           : 0;    // Force alignment to next boundary.  
   unsigned nMonth    : 5;    // 0..12  (5 bits)  
   unsigned nYear     : 8;    // 0..100 (8 bits)  
};  
```  
  
 则内存布局如下图中所示。  
  
 ![与零 & #45 的 Date 对象的布局; 长度位域](../cpp/media/vc38uq2.png "vc38UQ2")  
带有零长度位域的数据对象的布局  
  
 位域的基础类型必须是整数类型、 中所述[基本类型](../cpp/fundamental-types-cpp.md)。  
  
## <a name="restrictions-on-bit-fields"></a>位域的限制  
 以下列表详述了位域的错误操作：  
  
1.  采用位域的地址。  
  
2.  使用位域初始化引用。  
  
## <a name="see-also"></a>另请参阅  
 [类和结构](../cpp/classes-and-structs-cpp.md)
