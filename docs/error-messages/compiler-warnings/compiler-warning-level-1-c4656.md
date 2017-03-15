---
title: "编译器警告 （等级 1） C4656 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4656
dev_langs:
- C++
helpviewer_keywords:
- C4656
ms.assetid: b5aaef74-2320-4345-a6ae-b813881a491c
caps.latest.revision: 7
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
ms.sourcegitcommit: 6cad5222fb0d97594d5b13b5cf8903eb2934ee88
ms.openlocfilehash: b88f2add0a7b8f365d3617b8eb28eecdfa5a0a26
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4656"></a>编译器警告（等级 1）C4656
symbol︰ 数据类型的新增功能或自上次生成以来已更改或以不同的方式在其他位置定义  
  
 你添加或更改了数据类型，使其成为自上次成功生成后的源代码中的新类型。 “编辑并继续”不支持对现有数据类型的更改。  
  
 此警告将始终后跟[错误 C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)。 有关详细信息，请参阅[支持的代码更改](/visualstudio/debugger/supported-code-changes-cpp)。  
  
### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>若要在不结束当前调试会话的情况下删除此警告  
  
1.  将数据类型改回其在发生错误前的状态。  
  
2.  在“调试”  菜单中选择“应用代码更改” 。  
  
### <a name="to-remove-this-error-without-changing-your-source-code"></a>若要在不更改源代码的情况下删除此错误  
  
1.  在“调试”  菜单上，选择“停止调试” 。  
  
2.  在“生成”  菜单上，选择“生成” 。
