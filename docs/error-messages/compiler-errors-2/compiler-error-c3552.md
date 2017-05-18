---
title: "编译器错误 C3552 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3552
dev_langs:
- C++
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
caps.latest.revision: 4
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
ms.openlocfilehash: ae268ae3c0d7857aa2c2cbafe9e158656f657f1a
ms.contentlocale: zh-cn
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3552"></a>编译器错误 C3552
“typename”: 后指定返回类型不能包含“auto”  
  
 如果你使用 `auto` 关键字作为函数返回类型的占位符，必须提供后指定返回类型。 但是，不能使用其他 `auto` 关键字来指定后指定返回类型。 例如，下述代码片段产生错误 C3552。  
  
 `auto myFunction->auto; // C3552`
