---
title: "链接器命令行语法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- linker [C++], syntax
- linker command line [C++]
- LINK tool [C++], command-line syntax
ms.assetid: e2a31e17-77bd-4e74-9305-75b105b26539
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3ce42aa031b91d5a4ec21ed14ac7cb47643e1325
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-command-line-syntax"></a>链接器命令行语法
若要运行链接。EXE，使用以下命令语法：  
  
```  
LINK arguments  
```  
  
 `arguments`包括选项和文件名并可以按任意顺序指定。 选项是首先处理，则文件。 使用一个或多个空格或制表符分隔自变量。  
  
> [!NOTE]
>  你只能从 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 命令提示符启动此工具。 不能从系统命令提示符或从文件资源管理器启动此工具。  
  
 命令行中上, 一个选项选项说明符组成，短划线 （-） 或正斜杠 （/） 后, 接选项的名称。 选项名不能缩写。 某些选项带自变量，冒号 （:） 后指定。 不包含空格或选项卡中所允许的选项规范，除 /COMMENT 选项中带引号的字符串中。 以十进制或 C 语言表示法指定数值自变量。 选项名及其关键字或文件名参数不区分大小写，但作为自变量的标识符区分大小写。  
  
 要传递给链接器文件，请在链接命令后命令行上指定文件名。 你可以使用文件名，指定的绝对或相对路径，并可以在文件名中使用通配符。 如果省略圆点 （.） 和文件扩展名，链接假定.obj 为了查找该文件。 链接不使用文件名扩展或在缺乏来作出假设文件; 内容它会通过检查，确定文件的类型，并相应地对其进行处理。  
  
 link.exe 将返回零成功 （没有错误）。  否则，链接器返回停止链接的错误号。  例如，如果链接器生成 LNK1104，则链接器将返回 1104年。  相应地，链接器返回的错误的最低错误数目为 1000年。  返回值为 128 表示操作系统或.config 文件; 存在配置问题加载程序不加载 link.exe 或 c2.dll。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)