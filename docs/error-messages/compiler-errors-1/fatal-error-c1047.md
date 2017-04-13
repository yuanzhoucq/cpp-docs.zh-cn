---
title: "错误 C1047 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1047
dev_langs:
- C++
helpviewer_keywords:
- C1047
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
caps.latest.revision: 5
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
ms.openlocfilehash: bee5dd89bf6ef92445466b12d79be5ba39d9cb5b
ms.lasthandoff: 04/12/2017

---
# <a name="fatal-error-c1047"></a>错误 C1047
对象或库文件“file”是使用比创建其他对象所用编译器旧的编译器创建的；请重新生成旧的对象和库  
  
 当使用 **/LTCG** 生成的对象文件或库链接在一起，而这些对象文件或库是用不同版本的 Visual C++ 工具集生成的，则会导致 C1047。  
  
 当你开始使用新版本的编译器，而不完全重新生成现有对象文件或库时，可能出现这种情况。  
  
 若要解决 C1047，请重新生成所有对象文件或库。
