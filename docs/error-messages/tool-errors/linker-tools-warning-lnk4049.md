---
title: "链接器工具警告 LNK4049 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4049
dev_langs:
- C++
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f44634bd99e485e444ffe9cee7747f31374becf4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4049"></a>链接器工具警告 LNK4049
本地定义的符号 symbol 导入  
  
 符号是同时从导出和导入到程序。  
  
 当你通过使用声明符号时，链接器会生成此警告`__declspec(dllexport)`存储类特性在一个对象文件中，通过使用引用该`__declspec(dllimport)`中另一个属性。  
  
 警告 LNK4049 是的更多常规版本[链接器工具警告 LNK4217](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md)。 它不能确定哪个函数从引用的导入的符号时，链接器将生成警告 LNK4049。  
  
 下面生成 LNK4049 而不是 LNK4217 的常见情形是：  
  
-   执行增量链接使用[/增量](../../build/reference/incremental-link-incrementally.md)选项。  
  
-   通过执行全程序优化[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)选项。  
  
 若要解决 lnk4049 问题，请尝试以下项之一：  
  
-   删除`__declspec(dllimport)`名称从触发 LNK4049 的符号的前向声明的声明。 你可以通过使用来搜索符号中二进制图像**DUMPBIN**实用程序。 **DUMPBIN/符号**交换机显示 COFF 符号表中的映像。 有关详细信息**DUMPBIN**实用程序，请参阅[DUMPBIN 参考](../../build/reference/dumpbin-reference.md)。  
  
-   临时禁用增量链接和全程序优化。 重新编译应用程序将生成警告 LNK4217，将包括导入的符号已从中引用的函数的名称。 删除`__declspec(dllimport)`声明从导入的符号和启用增量链接或根据需要的全程序优化。  
  
 尽管最终生成的代码将正常运行，则生成调用导入的函数的代码是效率低于直接调用该函数。 使用选项进行编译时，将不会出现此警告[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 有关详细信息导入和导出数据声明，请参阅[dllexport、 dllimport](../../cpp/dllexport-dllimport.md)。  
  
## <a name="example"></a>示例  
 链接的以下两个模块将生成 LNK4049。 第一个模块生成包含单个导出的函数的对象文件。  
  
```  
// LNK4049a.cpp  
// compile with: /c  
  
__declspec(dllexport) int func()   
{  
   return 3;  
}  
```  
  
## <a name="example"></a>示例  
 第二个模块生成包含中的第一个模块，以及对此函数在调用导出的函数的前向声明的对象文件`main`函数。 链接与第一个模块此模块将生成 LNK4049。 删除`__declspec(dllimport)`声明将解决此警告。  
  
```  
// LNK4049b.cpp  
// compile with: /link /WX /LTCG LNK4049a.obj  
// LNK4049 expected  
  
__declspec(dllimport) int func();  
// try the following line instead  
// int func();  
  
int main()  
{  
   return func();  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [链接器工具警告 LNK4217](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md)   
 [dllexport、dllimport](../../cpp/dllexport-dllimport.md)