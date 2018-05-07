---
title: 命令行警告 D9027 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9027
dev_langs:
- C++
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfe2493290c4e4cc5b744136b8e7036c6559220a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="command-line-warning-d9027"></a>命令行警告 D9027
源文件\<文件名 > 被忽略  
  
 CL.exe 忽略输入的源文件。  
  
 此警告可能引起 /Fo 选项和带有 /c 选项的命令行上输出文件名之间留一个空格。 例如：  
  
```  
cl /c /Fo output.obj input.c   
```  
  
 因为 /Fo 之间没有空格和`output.obj`，CL.exe 采用`output.obj`作为输入文件的名称。 若要解决此问题，请删除该空格：  
  
```  
cl /c /Fooutput.obj input.c   
```