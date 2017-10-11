---
title: "错误 C1084 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1084
dev_langs:
- C++
helpviewer_keywords:
- C1084
ms.assetid: b2f273ef-3a14-4d5f-8ce0-7a11a0388fe6
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: caf1e64e91871087c9e47860a41c2824a811295a
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1084"></a>错误 C1084
无法读取 filetype 文件：“file”: 消息  
  
 此错误通常是由编译器无法执行内部系统 API 调用造成的。 显示当遇到此错误的消息通常通过以下任一方法生成[_wcserror_s](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)或[FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351.aspx)。  
  
 执行以下步骤可帮助解决 C1084 错误：  
  
-   请确保指定的文件存在。  
  
-   请确保设置了访问指定文件所需的相应权限。  
  
-   确保命令行语法遵从中所述的规则[编译器命令行语法](../../build/reference/compiler-command-line-syntax.md)。  
  
-   另请确保环境变量**TMP**和**TEMP**经过适当的组，以及适当的权限才能访问这些环境变量所引用的目录。 此外确保按所引用的驱动器**TMP**和**TEMP**环境变量包含足够的可用空间量。  
  
-   如果消息指出“文件号错误”，说明指定的文件在后台进行编译的同时，可能已在前台关闭。  
  
 执行上面的诊断后，请执行干净的生成。
