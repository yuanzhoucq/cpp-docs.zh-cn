---
title: "&lt;请参阅&gt;（Visual c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <see>
- see
dev_langs: C++
helpviewer_keywords:
- <see> C++ XML tag
- see C++ XML tag
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 15e1aedefe6d20c181ff208f76a61f49e15f5214
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ltseegt-visual-c"></a>&lt;请参阅&gt;（Visual c + +）
通过 \<see> 标记可以从文本内指定链接。 使用[ \<seealso >](../ide/seealso-visual-cpp.md)以指示你可能想要的另请参阅部分中显示的文本。  
  
## <a name="syntax"></a>语法  
  
```  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a>参数  
 `member`  
 对可从当前编译环境调用的成员或字段的引用。  将名称括在单引号或双引号中。  
  
 编译器会检查给定的代码元素存在，并解析`member`为在输出 XML 中的元素名称。  如果编译器没有找到 `member`，它会发出警告。  
  
## <a name="remarks"></a>备注  
 使用 [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。  
  
 请参阅[\<摘要 >](../ide/summary-visual-cpp.md)有关的使用示例\<请参阅 >。  
  
 Visual C++ 编译器将尝试通过文档注释在一次处理中解决 cref 引用。  因此，如果使用 C++ 查找规则，编译器找不到符号，引用将被标记为未解析。 请参阅[ \<seealso >](../ide/seealso-visual-cpp.md)有关详细信息。  
  
## <a name="example"></a>示例  
 下面的示例显示如何建立 cref 引用泛型类型，以便编译器将解析引用。  
  
```  
// xml_see_cref_example.cpp  
// compile with: /LD /clr /doc  
// the following cref shows how to specify the reference, such that,  
// the compiler will resolve the reference  
/// <see cref="C{T}">  
/// </see>  
ref class A {};  
  
// the following cref shows another way to specify the reference,   
// such that, the compiler will resolve the reference  
/// <see cref="C < T >"/>  
  
// the following cref shows how to hard-code the reference  
/// <see cref="T:C`1">  
/// </see>  
ref class B {};  
  
/// <see cref="A">  
/// </see>  
/// <typeparam name="T"></typeparam>  
generic<class T>  
ref class C {};  
```  
  
## <a name="see-also"></a>请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)