---
title: "Container Class::erase | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
caps.latest.revision: 8
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
ms.openlocfilehash: 0a28e1ff0def707926a67e1fea77f40e9927c0c4
ms.lasthandoff: 02/24/2017

---
# <a name="container-classerase"></a>Container Class::erase
> [!NOTE]
>  本主题位于 Visual C++ 文档内，作为在 C++ 标准库内使用的容器的非功能性示例。 有关详细信息，请参阅 [C++ 标准库容器](../standard-library/stl-containers.md)。  
  
 删除元素。  
  
## <a name="syntax"></a>语法  
  
```  
 
    iterator erase(
    iterator _Where);

iterator erase(
    iterator first,  
    iterator last);
```  
  
## <a name="remarks"></a>备注  
 第一个成员函数将移除 _*Where*** 所指向的受控序列的元素。** 第二个成员函数将移除范围 [` first`、` last`) 中的受控序列的元素。 两者都返回一个迭代器，指定已移除的任何元素之外保留的第一个元素或 [end](../standard-library/container-class-end.md)（若此类元素不存在）。  
  
 成员函数仅在复制操作引发异常时才引发异常。  
  
## <a name="see-also"></a>另请参阅  
 [Sample Container 类](../standard-library/sample-container-class.md)

