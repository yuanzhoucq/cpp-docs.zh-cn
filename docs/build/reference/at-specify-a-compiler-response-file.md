---
title: '@ （指定编译器响应文件） |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '@'
dev_langs:
- C++
helpviewer_keywords:
- response files, C/C++ compiler
- '@ compiler option'
- cl.exe compiler, specifying response files
ms.assetid: 400fffee-909d-4f60-bf76-45833e822685
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f291ed9a0ccc86ea1ef6fe6703205d76cdcd0fa1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369573"
---
# <a name="-specify-a-compiler-response-file"></a>@（指定编译器响应文件）
指定编译器响应文件。  
  
## <a name="syntax"></a>语法  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>自变量  
 `response_file`  
 包含编译器命令的文本文件。  
  
## <a name="remarks"></a>备注  
 响应文件可以包含的任何命令都将在命令行上指定。 如果命令行自变量超过 127 个字符，这可能很有用。  
  
 不能指定**@** 选项从响应文件中。 也就是说，响应文件不能嵌入另一个响应文件。  
  
 从命令行中，你可以指定任意数量的响应文件选项 (例如， `@respfile.1 @respfile.2`) 根据需要。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
-   响应文件中不能指定从开发环境，并且必须在命令行中指定。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   不能以编程方式更改此编译器选项。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)