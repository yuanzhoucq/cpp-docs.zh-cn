---
title: "LINK 命令文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: link
dev_langs: C++
helpviewer_keywords:
- syntax, LINK command files
- command files [C++]
- LINK tool [C++]
- text files, passing arguments to LINK
- LINK tool [C++], command-line syntax
- command files [C++], LINK
ms.assetid: 7154511c-32b9-4e5b-a515-3922fa9de48e
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2b6543cbb54dc982b1e55be8c0c554a429410b78
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="link-command-files"></a>LINK 命令文件
可以将命令行自变量传递到命令文件形式的链接。 若要指定到链接器命令文件，请使用以下语法：  
  
```  
LINK @commandfile  
```  
  
 `commandfile`是文本文件的名称。 之间允许有空格或制表符 at 符号 (@) 和文件名。 不存在默认扩展;您必须指定完整的文件名，包括任何扩展。 不能使用通配符。 你可以使用文件名指定的绝对或相对路径。 链接不使用环境变量来搜索该文件。  
  
 在命令文件中，自变量可由分隔空格或制表符 （在命令行中） 和由换行符。  
  
 可以在命令文件中指定的命令行全部或部分。 你可以使用多个 LINK 命令中的命令文件。 LINK 接受命令文件输入，如同它在命令行上的位置中指定。 不能嵌套命令文件。 链接将回显命令文件的内容，除非[/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)指定选项。  
  
## <a name="example"></a>示例  
 以下命令以生成 DLL 在单独的命令文件中传递的对象文件和库的名称，并将第三个命令文件用于 /EXPORTS 选项：  
  
```  
link /dll @objlist.txt @liblist.txt @exports.txt  
```  
  
## <a name="see-also"></a>另请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)