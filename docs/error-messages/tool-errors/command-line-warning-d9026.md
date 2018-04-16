---
title: "命令行警告 D9026 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- D9026
dev_langs:
- C++
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9127ad1887d476e5460798f806c2db1ff3144de3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="command-line-warning-d9026"></a>命令行警告 D9026
选项将应用于整个命令行  
  
 指定文件名后，在命令中指定一个选项。 选项已应用到它前面的文件。  
  
 例如，在该命令  
  
```  
CL verdi.c /G5 puccini.c  
```  
  
 将使用用 /G5 选项，而不是 /G4 默认编译文件 VERDI.c。  
  
 此行为是不同于某些早期版本中，应用仅指定文件名，从而导致 VERDI.c 之前的选项正在编译使用/G4 和 PUCCINI.c 正在编译使用用 /G5。