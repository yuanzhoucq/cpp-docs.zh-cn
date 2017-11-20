---
title: "命令行警告 D9041 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: D9041
dev_langs: C++
helpviewer_keywords: D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9f80de8e9bbbf7c754ac8e13061ef3ae50c4715a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="command-line-warning-d9041"></a>命令行警告 D9041
无效的值 'value' 的 '/ 选项';假设 'value';添加 / 分析到命令行选项时指定此警告  
  
 代码分析警告编号已添加到**/wd**， **/we**， **/wo**，或**/wl**而无需还指定的命令行选项**/ 分析**命令行选项。 若要更正此错误，请添加**/ 分析**命令行选项或从相应删除无效的警告编号**/w**命令行选项。  
  
## <a name="example"></a>示例  
 下面的命令行示例将生成警告 D9041:  
  
```  
cl /EHsc /LD /wd6001 filename.cpp  
```  
  
 若要解决此警告，添加**/ 分析**命令行选项。 如果**/ 分析**不是支持你的编译器版本上，删除无效的警告编号，从**/wd**选项。  
  
## <a name="see-also"></a>另请参阅  
 [命令行错误 D8000 到 D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)   
 [编译器选项](../../build/reference/compiler-options.md)