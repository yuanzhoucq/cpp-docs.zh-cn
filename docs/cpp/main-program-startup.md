---
title: "main：程序启动 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc.main.startup"
  - "_tmain"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tmain 函数"
  - "入口点, 程序"
  - "主函数, 程序启动"
  - "程序启动 [C++]"
  - "启动代码, 主函数"
  - "wmain 函数"
ms.assetid: f9581cd6-93f7-4bcd-99ec-d07c3c107dd4
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# main：程序启动
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

名为 `main` 的特殊函数是所有 C 和 [!INCLUDE[TLA#tla_cpp](../cpp/includes/tlasharptla_cpp_md.md)] 程序的执行起点。  如果您要编写遵循 [!INCLUDE[TLA#tla_unicode](../cpp/includes/tlasharptla_unicode_md.md)] 编程模型的代码，则可使用 `wmain`（它是 `main` 的宽字符版本）。  
  
 `main` 函数未由编译器预定义。  必须在程序文本中提供此函数。  
  
 `main` 的声明语法为  
  
```  
int main();  
```  
  
 或（可选）  
  
```  
int main(int argc, char *argv[], char *envp[]);  
```  
  
## Microsoft 专用  
 `wmain` 的声明语法如下所示：  
  
```  
int wmain( );  
```  
  
 或（可选）  
  
```  
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);  
```  
  
 还可以使用 TCHAR.h 中定义的 `_tmain`。  除非定义了 \_UNICODE，否则 `_tmain` 将解析为 `main`。  在该示例中，`_tmain` 将解析为 `wmain`。  
  
 或者，`main` 和 `wmain` 函数可以声明为返回 `void`（没有返回值）。  如果将 `main` 或 `wmain` 声明为返回 `void`，则无法使用 [return](../cpp/return-statement-in-program-termination-cpp.md) 语句将退出代码返回到父进程或操作系统中。  若要在将 `main` 或 `wmain` 声明为 `void` 时返回退出代码，则必须使用 [exit](../cpp/exit-function.md) 函数。  
  
## 结束 Microsoft 专用  
 `argc` 和 `argv` 的类型由语言定义。  名称 `argc`、`argv` 和 `envp` 是传统的，但编译器不需要这些名称。  有关详细信息及示例，请参阅[参数定义](../cpp/argument-definitions.md)。  
  
## 请参阅  
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [使用 wmain 代替 main](../cpp/using-wmain-instead-of-main.md)   
 [main 函数限制](../cpp/main-function-restrictions.md)