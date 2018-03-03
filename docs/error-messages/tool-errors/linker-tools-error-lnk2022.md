---
title: "链接器工具错误 LNK2022 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2022
dev_langs:
- C++
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7ca45ed3cd83a3fc81a6dad8fdcec5aee3232c6a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2022"></a>链接器工具错误 LNK2022  
  
> 元数据操作失败 (*HRESULT*): *error_message*  
  
链接器在合并元数据时检测到错误。 若要成功链接，必须解决元数据错误。  
  
若要诊断此问题的一种方法是运行**ildasm-令牌**中列出的令牌在对象文件，以了解哪些类型具有上`error_message`，并查找不同之处。  在元数据，具有相同名称的两种不同类型无效，即使只是 LayoutType 属性不相同。  
  
其中一个原因 LNK2022 就是当具有相同的名称，但具有冲突定义的多个编译单位中存在的类型 （如结构） 和与编译时[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。  在这种情况下，请确保该类型中所有编译单位具有相同的定义。  中列出的类型名称`error_message`。  
  
LNK2022 的另一个可能原因是当链接器在不是对编译器指定了在不同的位置找到的元数据文件 (与[#using](../../preprocessor/hash-using-directive-cpp.md) )。 确保元数据文件（.dll 或 .netmodule）在传递给链接器时与传递给编译器时位于相同的位置。  
  
生成 ATL 应用程序，使用宏时`_ATL_MIXED`如果中至少一个使用在所有编译单位，所需。  
  
## <a name="example"></a>示例  
  
下面的示例定义了空的类型。  
  
```cpp  
// LNK2022_a.cpp  
// compile with: /clr /c  
public ref class Test {};  
```  
  
## <a name="example"></a>示例  
  
此示例演示不能链接两个源的代码文件包含类型的名称相同但不同的定义。  
  
下面的示例生成 LNK2022。  
  
```cpp  
// LNK2022_b.cpp  
// compile with: LNK2022_a.cpp /clr /LD   
// LNK2022 expected  
public ref class Test {  
   void func() {}  
   int var;  
};  
```