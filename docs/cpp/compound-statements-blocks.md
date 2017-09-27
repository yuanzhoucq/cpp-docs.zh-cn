---
title: "复合语句 （块） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '}'
- '{'
dev_langs:
- C++
helpviewer_keywords:
- blocks, about blocks
- compound statements
ms.assetid: 23855939-7430-498e-8936-0c70055ea701
caps.latest.revision: 6
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
ms.openlocfilehash: 9dc28fde0ab2cf5b21771347554d0c664b7f462d
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="compound-statements-blocks"></a>复合语句（块）
复合语句包含零个或多个语句括在大括号中 (**{}**)。 可以在任何期望语句出现的位置使用复合语句。 复合语句通常称为“块”。  
  
## <a name="syntax"></a>语法  
  
```  
  
{ [ statement-list ] }  
```  
  
## <a name="remarks"></a>备注  
 下面的示例使用复合语句作为*语句*属于**如果**语句 (请参阅[if 语句](../cpp/if-else-statement-cpp.md)有关语法的详细信息):  
  
```  
if( Amount > 100 )  
{  
    cout << "Amount was too large to handle\n";  
    Alert();  
}  
else  
{
    Balance -= Amount;  
}
```  
  
> [!NOTE]
>  由于声明是一条语句，因此声明可以是中的语句之一*语句列表*。 因此，复合语句内声明的名称（而不是显式声明为静态的名称）具有局部范围和（对于对象）生存期。 请参阅[作用域](../cpp/scope-visual-cpp.md)有关处理带局部范围的名称的详细信息。  
  
## <a name="see-also"></a>另请参阅  
 [ 语句概述](../cpp/overview-of-cpp-statements.md)
