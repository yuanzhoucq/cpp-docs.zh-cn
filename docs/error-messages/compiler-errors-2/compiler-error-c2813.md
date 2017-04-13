---
title: "编译器错误 C2813 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- C2813
ms.assetid: 6cf2135f-7b82-42d1-909a-5e864308a09c
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: fc5f5437751abf6bcb11299e8484a199275db970
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2813"></a>编译器错误 C2813
\#导入不支持 /mp  
  
 如果在编译器命令中指定，则会发出 C2813 **/MP**编译器选项，并且编译，以及一个或多个文件的两个或多个文件包含[#import](../../preprocessor/hash-import-directive-cpp.md)预处理器指令。 [#Import](../../preprocessor/hash-import-directive-cpp.md)指令从指定的类型库中的类型生成 c + + 类，然后将这些类写入两个标头文件。 [#Import](../../preprocessor/hash-import-directive-cpp.md)指令不支持，因为如果多个编译单元导入相同的类型库，当用户尝试同时写入相同的标头文件，这些单元产生冲突。  
  
 此编译器错误和**/MP**编译器选项是中的新增[!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)]。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2813。 “compile with:”注释中的命令行向编译器指示使用 **/MP** 和 **/c** 编译器选项编译多个文件。 至少一个文件包含[#import](../../preprocessor/hash-import-directive-cpp.md)指令。 为了测试此示例，我们对相同文件使用了两次。  
  
```  
// C2813.cpp  
// compile with: /MP /c C2813.cpp C2813.cpp  
#import "C:\windows\system32\stdole2.tlb"   // C2813  
int main()   
{  
}  
```
