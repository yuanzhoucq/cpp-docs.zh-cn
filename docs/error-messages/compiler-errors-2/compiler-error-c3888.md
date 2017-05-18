---
title: "编译器错误 C3888 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3888
dev_langs:
- C++
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 4b85385c97f5873c1b370cd72f0866439263f787
ms.contentlocale: zh-cn
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3888"></a>编译器错误 C3888
“name”：C++/CLI 不支持与此 literal 数据成员关联的常量表达式  
  
 *名称*与声明的数据成员[文本](../../windows/literal-cpp-component-extensions.md)关键字初始化编译器不支持的值。 编译器仅支持常量整型、枚举或字符串类型。 **C3888** 错误可能的原因是数据成员是使用字节数组初始化的。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  检查声明的 literal 数据成员是否是支持的类型。  
  
## <a name="see-also"></a>另请参阅  
 [文本](../../windows/literal-cpp-component-extensions.md)
