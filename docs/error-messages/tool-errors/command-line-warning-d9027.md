---
title: "命令行警告 D9027 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- D9027
dev_langs:
- C++
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
caps.latest.revision: 6
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 7d569243a6d0d1669a8964ab9c419cb0e7428ba9
ms.contentlocale: zh-cn
ms.lasthandoff: 04/04/2017

---
# <a name="command-line-warning-d9027"></a>命令行警告 D9027
源文件\<filename 1> 忽略  
  
 CL.exe 忽略输入的源文件。  
  
 此警告可能引起 /Fo 选项和带有 /c 选项的命令行上输出文件名之间留一个空格。 例如:   
  
```  
cl /c /Fo output.obj input.c   
```  
  
 因为 /Fo 之间没有空格和`output.obj`，CL.exe 采用`output.obj`作为输入文件的名称。 若要解决此问题，请删除该空格︰  
  
```  
cl /c /Fooutput.obj input.c   
```
