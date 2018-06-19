---
title: -c （链接的情况下进行编译） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /c
dev_langs:
- C++
helpviewer_keywords:
- suppress link
- cl.exe compiler, compiling without linking
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 8017fc3d-e5dd-4668-a1f7-3120daa95d20
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86bd1ddcb6d44cfa433d4119f90eb02695089aa4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32370431"
---
# <a name="c-compile-without-linking"></a>/c（在不链接的情况下进行编译）
可防止对链接的自动调用。  
  
## <a name="syntax"></a>语法  
  
```  
/c  
```  
  
## <a name="remarks"></a>备注  
 使用编译 **/c**只创建.obj 文件。 使用正确的文件和选项来执行生成的链接阶段中，必须显式调用链接。  
  
 在开发环境中创建任何内部项目使用 **/c**默认情况下的选项。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
-   此选项不可用从开发环境中。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   若要以编程方式设置此编译器选项，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileOnly%2A>。  
  
## <a name="example"></a>示例  
 下面的命令行创建 FIRST.obj 和 SECOND.obj 对象文件。THIRD.obj 将被忽略。  
  
```  
CL /c FIRST.C SECOND.C THIRD.OBJ  
```  
  
 若要创建可执行文件，必须调用链接：  
  
```  
LINK firsti.obj second.obj third.obj /OUT:filename.exe  
```  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)