---
title: operator&gt; (&lt;sample container&gt;) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::operator>
- std.>
- std.operator>
- operator>
- std::>
- '>'
dev_langs:
- C++
helpviewer_keywords:
- '> operator, comparing specific objects'
- operator >
ms.assetid: 49bd417a-3305-4ffa-9884-39d3904ed87d
caps.latest.revision: 9
author: corob-msft
ms.author: corob
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
translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 06eff0e3674772ac00716fdd4afb2b3e0c1a7bd7
ms.lasthandoff: 02/24/2017

---
# <a name="operatorgt-ltsample-containergt"></a>operator&gt; (&lt;sample container&gt;)
> [!NOTE]
>  本主题位于 Visual C++ 文档内，作为在 C++ 标准库内使用的容器的非功能性示例。 有关详细信息，请参阅 [C++ 标准库容器](../standard-library/stl-containers.md)。  
  
 重载 **operator>** 以比较 [Container](../standard-library/sample-container-class.md) 模板类的两个对象。  
  
## <a name="syntax"></a>语法  
  
```  
 
    template <class Ty>  
bool operator*gt;(
    const Container <Ty>& left,  
    const Container <Ty>& right);
```  
  
## <a name="return-value"></a>返回值  
 返回 _*Right* < \_*Left*。  
  
## <a name="see-also"></a>另请参阅  
 [\<sample container>](../standard-library/sample-container.md)


