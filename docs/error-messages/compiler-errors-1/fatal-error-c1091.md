---
title: "错误 C1091 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1091
dev_langs:
- C++
helpviewer_keywords:
- C1091
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
caps.latest.revision: 8
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
ms.openlocfilehash: f014e2b9d34cdac17adefe88c4947ee5fb66cfcc
ms.contentlocale: zh-cn
ms.lasthandoff: 04/12/2017

---
# <a name="fatal-error-c1091"></a>错误 C1091
编译器限制：字符串长度超过“length”个字节  
  
 字符串常量超过当前的字符串长度限制。  
  
 你可能想要将静态字符串拆分为两个 （或多个） 的变量和使用[strcpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)作为一部分声明时或在运行时联接结果。
