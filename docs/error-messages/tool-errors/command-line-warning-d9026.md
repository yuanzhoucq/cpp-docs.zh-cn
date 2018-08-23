---
title: 命令行警告 D9026 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9026
dev_langs:
- C++
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e2d99573ee46c51178cc2fe995fa0f526b800f9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299833"
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