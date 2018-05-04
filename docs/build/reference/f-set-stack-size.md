---
title: -F （设置堆栈大小） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /f
dev_langs:
- C++
helpviewer_keywords:
- set stack size compiler option
- F compiler option [C++]
- -F compiler option [C++]
- /F compiler option [C++]
- stack, setting size
ms.assetid: 17320b6f-8305-445b-9ec2-75833f4b29e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed0ad03d18493cc5618f9aad2a16b07e4a01717f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="f-set-stack-size"></a>/F（设置堆栈大小）
以字节为单位设置程序堆栈大小。  
  
## <a name="syntax"></a>语法  
  
```  
/F number  
```  
  
## <a name="arguments"></a>自变量  
 `number`  
 堆栈大小 （字节）。  
  
## <a name="remarks"></a>备注  
 如果不使用此选项的堆栈大小默认为 1 MB。 `number`自变量可以是以十进制或 C 语言表示法。 参数可以介于 1 到链接器接受的最大堆栈大小。 链接器将指定的值与最接近的 4 个字节向上舍入。 之间的空间 **/F**和`number`是可选的。  
  
 你可能需要增加的堆栈大小，如果你的程序获取堆栈溢出消息。  
  
 此外可以设置堆栈大小：  
  
-   使用 **/堆栈**链接器选项。 有关详细信息，请参阅[/堆栈](../../build/reference/stack.md)。  
  
-   使用 EDITBIN 的.exe 文件。 有关详细信息，请参阅[EDITBIN 参考](../../build/reference/editbin-reference.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  点击“命令行”  属性页。  
  
4.  在 **“附加选项”** 框中键入编译器选项。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)