---
title: "错误 C1103 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1103
dev_langs:
- C++
helpviewer_keywords:
- C1103
ms.assetid: 9d276939-9c47-4235-9d20-76b8434f9731
caps.latest.revision: 6
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
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: e750c21ab6f9d3882413a83731c0fa2787f8fe47
ms.lasthandoff: 04/12/2017

---
# <a name="fatal-error-c1103"></a>错误 C1103
导入 progid 时遇到错误：“message”  
  
 导入类型库时编译器检测到问题。  例如，你不能使用 progid 指定类型库，同时还指定 `no_registry`。  
  
 有关详细信息，请参阅[#import 指令](../../preprocessor/hash-import-directive-cpp.md)。  
  
 下面的示例生成 C1103：  
  
```  
// C1103.cpp  
#import "progid:a.b.id.1.5" no_registry auto_search   // C1103  
```
