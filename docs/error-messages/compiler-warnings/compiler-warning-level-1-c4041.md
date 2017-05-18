---
title: "编译器警告 （等级 1） C4041 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4041
dev_langs:
- C++
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
caps.latest.revision: 7
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
ms.openlocfilehash: f6578b938a5b8fcecd0bcb3f9a60134acaa30131
ms.contentlocale: zh-cn
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4041"></a>编译器警告（等级 1）C4041
编译器限制 : 正在终止浏览器输出  
  
 浏览器信息超出了编译器限制。  
  
 此警告可能引起编译[/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) （浏览器信息包含局部变量）。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复  
  
1.  使用 /Fr（浏览器信息不含局部变量）进行编译。  
  
2.  禁用浏览器输出（不使用 /FR 或 /Fr 进行编译）。
