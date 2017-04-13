---
title: "编译器警告 （等级 1） C4953 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4953
dev_langs:
- C++
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
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
ms.openlocfilehash: d0b8ba97d493cb6e840be1023f7c6bd29a5cbd1a
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4953"></a>编译器警告（等级 1）C4953
在收集配置文件数据后已编辑过内联“function”，没有使用配置文件数据  
  
 当使用[/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)，编译器检测到后已重新编译输入的模块`/LTCG:PGINSTRUMENT`并且有一个函数 (***函数***)，进行了编辑，现有测试运行该函数标识作为的候选项内联。 但是，重新编译该模块后，此函数不再是内联的候选项。  
  
 此警告为信息性。 若要解决此警告，请运行 `/LTCG:PGINSTRUMENT`，重做所有测试，并运行 `/LTCG:PGOPTIMIZE`。  
  
 如果已使用 `/LTCG:PGOPTIMIZE` ，此警告将替换为一个错误。
