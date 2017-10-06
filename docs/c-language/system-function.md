---
title: "system 函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- system function
ms.assetid: 0786ccdc-20cd-4d96-b3d8-3230507c3066
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: b504aedc5ad11edf40d7b797529065757dfb58e6
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="system-function"></a>系统函数
**ANSI 4.10.4.5** system 函数执行字符串的内容和模式  
  
 system 函数执行内部操作系统命令，或者 C 程序中（而不是命令行中）的 .EXE、.COM（Windows NT 中的 .CMD）或 .BAT 文件。  
  
 系统函数查找命令解释器，它通常是 Windows NT 操作系统中的 CMD.EXE 或 Windows 中的 COMMAND.COM。 系统函数随后将自变量字符串传递到命令解释器。  
  
 有关详细信息，请参阅 [system、_wsystem](../c-runtime-library/reference/system-wsystem.md)。  
  
## <a name="see-also"></a>另请参阅  
 [库函数](../c-language/library-functions.md)
