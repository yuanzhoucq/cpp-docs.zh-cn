---
title: "为自己的类重载 &gt;&gt; 运算符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- operator>>
- operator>>, overloading for your own classes
- operator >>, overloading for your own classes
ms.assetid: 40dab4e0-3f97-4745-9cc8-b86e740fa246
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a895574b2277407ac907e8fd6cbd9fecfec1500d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="overloading-the-gtgt-operator-for-your-own-classes"></a>为自己的类重载 &gt;&gt; 运算符
输出流使用标准类型的提取 (`>>`) 运算符。 你可以为自己的类型编写相似的提取运算符；成功与否取决于对空格的精确使用。  
  
 下面是前文中列举的 `Date` 类的一个提取运算符示例：  
  
```  
istream& operator>> (istream& is, Date& dt)  
{  
    is>> dt.mo>> dt.da>> dt.yr;  
    return is;  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [输入流](../standard-library/input-streams.md)

