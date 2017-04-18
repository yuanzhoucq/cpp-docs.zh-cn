---
title: "编译器警告 （等级 1） C4952 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4952
dev_langs:
- C++
helpviewer_keywords:
- C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
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
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: fa48ab2f0e7a2a9d7675af5d2e88aa56b100f022
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4952"></a>编译器警告（等级 1）C4952
“function”：在程序数据库“pgd_file”中未找到配置文件数据  
  
 使用时[/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)，编译器检测到后已重新编译输入的模块`/LTCG:PGINSTRUMENT`并且有一个新函数 (***函数***) 存在。  
  
 此警告为信息性。 若要解决此警告，请运行 `/LTCG:PGINSTRUMENT`，重做所有测试，并运行 `/LTCG:PGOPTIMIZE`。  
  
 如果已使用 `/LTCG:PGOPTIMIZE` ，此警告将替换为一个错误。
