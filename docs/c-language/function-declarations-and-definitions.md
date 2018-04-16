---
title: "函数声明和定义 | Microsoft Docs"
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
- local declarations
- function definitions, function declarations
- declaring functions, function definitions
- internal declarations
- external declarations
- function prototypes, basics
- external linkage, function declarations
- declaring functions
ms.assetid: 43fd98eb-7441-4473-a5d9-fc88c75577f7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 65be3d2e59a9d672db18ba332d608fdf031f16e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="function-declarations-and-definitions"></a>函数声明和定义
函数原型确定了函数的名称、返回类型以及形参的类型和数量。 函数定义包括函数体。  
  
## <a name="remarks"></a>备注  
 函数声明和变量声明均可出现在函数定义的内部或外部。 函数定义中的所有声明应在“内部”或“局部”级别显示。 所有函数定义之外的声明应在“外部”、“全局”或“文件范围”级别显示。 变量定义（如声明）可在内部级别（在函数定义中）或在外部级别（在所有函数定义外）显示。 函数定义始终会在外部级别显示。 [函数定义](../c-language/c-function-definitions.md)中进一步讨论了函数定义。 [函数原型](../c-language/function-prototypes.md)中介绍了函数原型。  
  
## <a name="see-also"></a>请参阅  
 [源文件和源程序](../c-language/source-files-and-source-programs.md)