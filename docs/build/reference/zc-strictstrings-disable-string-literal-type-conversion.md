---
title: "/Zc:strictStrings（禁用字符串文本类型转换） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/Zc:strictStrings"
  - "strictStrings"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc 编译器选项 (C++)"
  - "/Zc:strictStrings"
  - "strictStrings"
  - "Zc 编译器选项 (C++)"
  - "-Zc 编译器选项 (C++)"
ms.assetid: b7eb3f3b-82c1-48a2-8e63-66bad7397b46
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /Zc:strictStrings（禁用字符串文本类型转换）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定后，编译器要求通过使用字符串文本初始化的指针符合严格的 `const` 限定。  
  
## 语法  
  
```  
/Zc:strictStrings[-]  
```  
  
## 备注  
 如果指定了 **\/Zc:strictStrings**，则编译器针对字符串文本（如类型“`const` `char` 的数组”或“`const` `wchar_t` 的数组”，具体取决于声明）强制执行标准 C\+\+ `const` 限定。  字符串文本不可变，并且尝试修改一个字符串文本的内容将导致在运行时出现访问冲突错误。  必须将字符串指针声明为 `const` 以通过使用字符串文本将其初始化，或使用显式 `const_cast` 以初始化非 `const` 指针。  或者默认情况下，如果指定了 **\/Zc:strictStrings\-**，则编译器不会针对通过使用字符串文本初始化的字符串指针强制执行标准 C\+\+ `const` 限定。  
  
 使用 **\/Zc:strictStrings** 选项来阻止编译错误代码。  此示例显示一个简单声明错误如何在运行时导致崩溃：  
  
```cpp  
// strictStrings_off.cpp  
// compile by using: cl /W4 strictStrings_off.cpp  
int main() {  
   wchar_t* str = L"hello";  
   str[2] = L'a'; // run-time error: access violation  
}  
```  
  
 当 **\/Zc:strictStrings** 处于启用状态时，相同的代码将报告 `str` 声明中的错误。  
  
```cpp  
// strictStrings_on.cpp  
// compile by using: cl /Zc:strictStrings /W4 strictStrings_on.cpp  
int main() {  
   wchar_t* str = L"hello"; // error: Conversion from string literal   
   // loses const qualifier  
   str[2] = L'a';   
}  
```  
  
 如果使用 `auto` 声明字符串指针，则编译器将为你创建正确的 `const` 指针类型声明。  尝试修改 `const` 指针的内容将由编译器报告为错误。  
  
> [!NOTE]
>  [!INCLUDE[cpp_dev12_long](../../build/reference/includes/cpp_dev12_long_md.md)] 中的标准 C\+\+ 库不支持调试生成中的 **\/Zc:strictStrings** 编译器选项。  如果在你的生成输出中看到多个 [C2665](../../error-messages/compiler-errors-2/compiler-error-c2665.md) 错误，则可能由此原因造成。  
  
 有关 Visual C\+\+ 中的一致性问题的详细信息，请参阅[非标准行为](../../cpp/nonstandard-behavior.md)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择 **C\/C\+\+** 文件夹。  
  
3.  选择**“命令行”**属性页。  
  
4.  修改**“附加选项”**属性以包含 `/Zc:strictStrings`，然后选择**“确定”**。  
  
## 请参阅  
 [\/Zc（一致性）](../../build/reference/zc-conformance.md)