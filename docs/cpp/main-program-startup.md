---
title: main： 程序启动 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- vc.main.startup
- _tmain
dev_langs:
- C++
helpviewer_keywords:
- program startup [C++]
- entry points, program
- wmain function
- _tmain function
- startup code, main function
- main function, program startup
ms.assetid: f9581cd6-93f7-4bcd-99ec-d07c3c107dd4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f78a122837fc2cb9a89083d5be8fd2b488c1772
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939219"
---
# <a name="main-program-startup"></a>main：程序启动
一个名为的特殊函数`main`是所有 C 和 C++ 程序的执行的起始点。 如果您要编写遵循 [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] 编程模型的代码，则可使用 `wmain`（它是 `main` 的宽字符版本）。  
  
 `main` 函数未由编译器预定义。 必须在程序文本中提供此函数。  
  
 `main` 的声明语法为  
  
```cpp 
int main();  
```  
  
 或（可选）  
  
```cpp 
int main(int argc, char *argv[], char *envp[]);  
```  
  
## <a name="microsoft-specific"></a>Microsoft 专用  
 `wmain` 的声明语法如下所示：  
  
```cpp 
int wmain( );  
```  
  
 或（可选）  
  
```cpp 
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);  
```  
  
 还可以使用 TCHAR.h 中定义的 `_tmain`。 除非定义了 _UNICODE，否则 `_tmain` 将解析为 `main`。 在该示例中，`_tmain` 将解析为 `wmain`。  
  
 或者，`main`并`wmain`函数可以声明为返回**void** （没有返回值）。 如果声明`main`或`wmain`为返回**void**，你不能使用退出代码返回到父进程或操作系统[返回](../cpp/return-statement-in-program-termination-cpp.md)语句。 若要返回退出代码时`main`或`wmain`声明为**void**，则必须使用[退出](../cpp/exit-function.md)函数。  
  
**结束 Microsoft 专用**  
 `argc` 和 `argv` 的类型由语言定义。 名称 `argc`、`argv` 和 `envp` 是传统的，但编译器不需要这些名称。 有关详细信息和示例，请参阅[自变量定义](../cpp/argument-definitions.md)。  
  
## <a name="see-also"></a>请参阅  
 [关键字](../cpp/keywords-cpp.md)   
 [使用 wmain 代替 main](../cpp/using-wmain-instead-of-main.md)   
 [main 函数限制](../cpp/main-function-restrictions.md)   
 [分析 C++ 命令行参数](../cpp/parsing-cpp-command-line-arguments.md)
