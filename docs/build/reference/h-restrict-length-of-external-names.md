---
title: -H （限制外部名称的长度） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /h
dev_langs:
- C++
helpviewer_keywords:
- public name length
- /H compiler option [C++]
- H compiler option [C++]
- external names
- -H compiler option [C++]
ms.assetid: de701dd3-ed04-4c88-8195-960d2520ec2e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0859c6770da56023df7ba7ba24094bea2e889319
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="h-restrict-length-of-external-names"></a>/H（限制外部名称长度）
已否决。 限制外部名称的长度。  
  
## <a name="syntax"></a>语法  
  
```  
/Hnumber  
```  
  
## <a name="arguments"></a>自变量  
 `number`  
 指定外部名称在程序中允许的最大长度。  
  
## <a name="remarks"></a>备注  
 默认情况下，外部 （公共） 名称的长度为 2047 个字符。 这适用于 C 和 c + + 程序。 使用 **/H**只能减少标识符最大允许长度，而不将其增加。 之间留一个空格 **/H**和`number`是可选的。  
  
 如果程序包含外部名称长度超过`number`，会忽略多余字符。 如果在编译而无需程序 **/H**且如果标识符包含多个 2047 个字符，则编译器将生成[致命错误 C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md)。  
  
 对长度的限制包括任何编译器创建的前导下划线 (_) 或 at 符号 (@)。 这些字符是标识符的一部分，并且占用有效位置。  
  
-   编译器将前导下划线 (_) 添加到由修改名称`__cdecl`（默认值） 和`__stdcall`调用约定和一个前导 at 符号 (@) 修改名称`__fastcall`调用约定。  
  
-   编译器将自变量大小信息追加到名称修改`__fastcall`和`__stdcall`调用约定，并将类型信息添加到 c + + 名称。  
  
 你可能会发现 **/H**有用：  
  
-   当你创建混合语言或可移植程序。  
  
-   如果你使用具有外部标识符的长度限制类的工具。  
  
-   如果想要限制的使用调试版本中的符号的空间量。  
  
 下面的示例演示如何使用 **/H**实际引入错误如果标识符长度，则限制太多：  
  
```cpp  
// compiler_option_H.cpp  
// compile with: /H5  
// processor: x86  
// LNK2005 expected  
void func1(void);  
void func2(void);  
  
int main() { func1(); }  
  
void func1(void) {}  
void func2(void) {}  
```  
  
 你还必须是使用时请小心 **/H**由于预定义的编译器标识符的选项。 如果最大标识符长度太小，某些预定义的标识符将为未解析，以及某些库函数调用。 例如，如果`printf`使用函数和选项 **/H5**指定在编译时，符号 **_prin**将创建以引用`printf`，这将不会找到和位于库中。  
  
 利用 **/H**与不兼容[/GL （全程序优化）](../../build/reference/gl-whole-program-optimization.md)。  
  
 **/H**选项自 Visual Studio 2005 年以来已弃用; 已增加最大长度限制和 **/H**不再需要。 不推荐使用的编译器选项的列表，请参阅**已弃用并删除的编译器选项**中[按类别列出的编译器选项](../../build/reference/compiler-options-listed-by-category.md)。  
  
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