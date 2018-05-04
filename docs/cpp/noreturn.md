---
title: noreturn |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- noreturn_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90fab865a02b7ad00bd25b6d74f2d19b2678875c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="noreturn"></a>noreturn
## <a name="microsoft-specific"></a>Microsoft 专用  
 此 `__declspec` 特性告知编译器函数不会返回。 因此，编译器了解到调用代码 **__declspec （noreturn)** 函数不可访问。  
  
 如果编译器找到带有不返回值的控制路径的函数，则它会生成警告 (C4715) 或错误消息 (C2202)。 如果因一个从不返回的函数导致无法到达控制路径，则可以使用 **__declspec （noreturn)** 阻止此警告或错误。  
  
> [!NOTE]
>  添加 **__declspec （noreturn)** 到预期返回的函数可以导致未定义的行为。  
  
## <a name="example"></a>示例  
 在下面的示例中，**其他**子句不包含 return 语句。  声明`fatal`作为 **__declspec （noreturn)** 可避免错误或警告消息。  
  
```  
// noreturn2.cpp  
__declspec(noreturn) extern void fatal () {}  
  
int main() {  
   if(1)  
     return 1;  
   else if(0)  
     return 0;  
   else  
     fatal();  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [__declspec](../cpp/declspec.md)   
 [关键字](../cpp/keywords-cpp.md)