---
title: "-Zc: strictStrings （禁用字符串文本类型转换） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /Zc:strictStrings
- strictStrings
dev_langs: C++
helpviewer_keywords:
- /Zc:strictStrings
- -Zc compiler options (C++)
- strictStrings
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: b7eb3f3b-82c1-48a2-8e63-66bad7397b46
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f316c5fc9209f968219d770a15e6576880b69954
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="zcstrictstrings-disable-string-literal-type-conversion"></a>/Zc:strictStrings（禁用字符串文本类型转换）
指定后，编译器要求通过使用字符串文本初始化的指针符合严格的 `const` 限定。  
  
## <a name="syntax"></a>语法  
  
```  
/Zc:strictStrings[-]  
```  
  
## <a name="remarks"></a>备注  
 如果**/zc: strictstrings**指定，则编译器强制执行标准 c + +`const`作为类型的字符串文字的资格要求数组`const char`或数组`const wchar_t`，则根据声明。 字符串文本不可变，并且尝试修改一个字符串文本的内容将导致在运行时出现访问冲突错误。 必须将字符串指针声明为 `const` 以通过使用字符串文本将其初始化，或使用显式 `const_cast` 以初始化非 `const` 指针。 默认情况下，或者如果**/Zc:strictStrings-**指定，编译器不强制执行标准 c + +`const`通过使用字符串文本初始化的字符串指针的限定资格。  
  
 使用**/zc: strictstrings**选项来阻止编译错误代码。 此示例显示一个简单声明错误如何在运行时导致崩溃：  
  
```cpp  
// strictStrings_off.cpp  
// compile by using: cl /W4 strictStrings_off.cpp  
int main() {  
   wchar_t* str = L"hello";  
   str[2] = L'a'; // run-time error: access violation  
}  
```  
  
 当**/zc: strictstrings**是启用，相同的代码报告中的声明的错误`str`。  
  
```cpp  
// strictStrings_on.cpp  
// compile by using: cl /Zc:strictStrings /W4 strictStrings_on.cpp  
int main() {  
   wchar_t* str = L"hello"; // error: Conversion from string literal   
   // loses const qualifier  
   str[2] = L'a';   
}  
```  
  
 如果使用 `auto` 声明字符串指针，则编译器将为你创建正确的 `const` 指针类型声明。 尝试修改 `const` 指针的内容将由编译器报告为错误。  
  
> [!NOTE]
>  中的 c + + 标准库[!INCLUDE[cpp_dev12_long](../../build/reference/includes/cpp_dev12_long_md.md)]不支持**/zc: strictstrings**编译器选项在调试生成。 如果你看到多个[C2665](../../error-messages/compiler-errors-2/compiler-error-c2665.md)中生成的错误输出，这可能是可能的原因。  
  
 有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**C/c + +**文件夹。  
  
3.  选择**命令行**属性页。  
  
4.  修改**其他选项**属性以包含`/Zc:strictStrings`，然后选择**确定**。  
  
## <a name="see-also"></a>请参阅  
 [/Zc（一致性）](../../build/reference/zc-conformance.md)