---
title: "读取范围 | Microsoft Docs"
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
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
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
translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 0892c38d6448ed28a309c8c9864d78dc9aeb4a28
ms.lasthandoff: 04/01/2017

---
# <a name="reading-ranges"></a>读取范围
**ANSI 4.9.6.2**：短划线 (-) 字符的解释，该字符既不是 `fscanf` 函数的 % [ 转换的扫描表中的第一个字符，也不是该表中的最后一个字符  
  
 下面的行  
  
```  
fscanf( fileptr, "%[A-Z]", strptr);  
```  
  
 将 A-Z 范围内的任意数目的字符读取到 `strptr` 指向的字符串中。  
  
## <a name="see-also"></a>另请参阅  
 [库函数](../c-language/library-functions.md)
