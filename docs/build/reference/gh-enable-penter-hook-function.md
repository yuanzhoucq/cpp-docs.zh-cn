---
title: -Gh （启用 _penter 挂钩函数） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _penter
dev_langs:
- C++
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _penter function
- -Gh compiler option [C++]
ms.assetid: 1510a082-8a0e-486e-a309-6add814b494f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 68497e4e760e1268a0175d5a68452678153896b8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373148"
---
# <a name="gh-enable-penter-hook-function"></a>/Gh（启用 _penter 挂钩函数）
导致调用`_penter`开头的每个方法或函数的函数。  
  
## <a name="syntax"></a>语法  
  
```  
/Gh  
```  
  
## <a name="remarks"></a>备注  
 `_penter`函数不是任何库的一部分，由你提供的定义是`_penter`。  
  
 除非你打算显式调用`_penter`，不需要提供原型。 函数必须看起来似乎具有以下原型，并且必须在进入时推送所有寄存器的内容，在退出时弹出未更改的内容：  
  
```  
void __declspec(naked) _cdecl _penter( void );  
```  
  
 此声明不是适用于 64 位项目。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  点击“命令行”  属性页。  
  
4.  在 **“附加选项”** 框中键入编译器选项。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="example"></a>示例  
 下面的代码，如果使用编译的 **/Gh**，演示如何`_penter`被调用两次; 一次输入函数时`main`，另一次输入函数时`x`。  
  
```  
// Gh_compiler_option.cpp  
// compile with: /Gh  
// processor: x86  
#include <stdio.h>  
void x() {}  
  
int main() {  
   x();  
}  
  
extern "C" void __declspec(naked) _cdecl _penter( void ) {  
   _asm {  
      push eax  
      push ebx  
      push ecx  
      push edx  
      push ebp  
      push edi  
      push esi  
    }  
  
   printf_s("\nIn a function!");  
  
   _asm {  
      pop esi  
      pop edi  
      pop ebp  
      pop edx  
      pop ecx  
      pop ebx  
      pop eax  
      ret  
    }  
}  
```  
  
```Output  
In a function!  
In a function!  
```  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)