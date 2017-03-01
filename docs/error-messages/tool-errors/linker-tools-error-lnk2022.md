---
title: "链接器工具错误 LNK2022 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2022
dev_langs:
- C++
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 84964b0a49b236bae056125de8155b18880eb378
ms.openlocfilehash: 91fb85679fd6c66bc97974912a2de688f494d5e9
ms.lasthandoff: 02/24/2017

---
# <a name="linker-tools-error-lnk2022"></a>链接器工具错误 LNK2022
元数据操作失败 (HRESULT): error_message  
  
 链接器在合并元数据时检测到错误。 必须解析元数据错误，链接才能成功。  
  
 若要诊断此问题的一种方法是运行**ildasm – 令牌**中列出这些标记在对象文件，以查找有哪些类型上`error_message`，并查找不同之处。  在元数据中具有相同名称的两种不同类型不正确，即使只是 LayoutType 属性不同。  
  
 其中一个原因 LNK2022 就是如果类型 （如结构） 存在于多个 compiland 与名称相同，但具有冲突定义和使用进行编译时[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。  在这种情况下，请确保该类型中所有 compiland 具有相同的定义。  中列出的类型名称`error_message`。  
  
 LNK2022 的另一个可能原因是当链接器在不是指定给编译器在不同的位置找到的元数据文件 (与[#using](../../preprocessor/hash-using-directive-cpp.md) )。 确保元数据文件（.dll 或 .netmodule）在传递给链接器时与传递给编译器时位于相同的位置。  
  
 在生成 ATL 应用程序，使用时[_ATL_MIXED](http://msdn.microsoft.com/Library/11b59a83-7098-43e2-9f7b-408299930966)如果中至少一个使用在所有 compiland 中必需。  
  
## <a name="example"></a>示例  
 下面的示例定义一个空类型。  
  
```  
// LNK2022_a.cpp  
// compile with: /clr /c  
public ref class Test {};  
```  
  
## <a name="example"></a>示例  
 此示例演示不能链接两个源代码文件包含类型的名称相同但不同的定义。  
  
 下面的示例生成 LNK2022。  
  
```  
// LNK2022_b.cpp  
// compile with: LNK2022_a.cpp /clr /LD   
// LNK2022 expected  
public ref class Test {  
   void func() {}  
   int var;  
};  
```
