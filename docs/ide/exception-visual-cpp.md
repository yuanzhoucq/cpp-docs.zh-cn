---
title: '&lt;exception&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- exception
- <exception>
dev_langs:
- C++
helpviewer_keywords:
- <exception> C++ XML tag
- exception C++ XML tag
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d3d5b7a89a3725ae9dee2065bcd21d8f114ca00
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323935"
---
# <a name="ltexceptiongt-visual-c"></a>&lt;exception&gt; (Visual C++)
\<exception> 标记让你指定可引发的异常。 这是适用于方法定义的标记。  
  
## <a name="syntax"></a>语法  
  
```  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a>参数  
 `member`  
 对当前编译环境中出现的一个异常的引用。 使用名称查找规则，编译器检查是否存在给定的异常，并将 `member` 转换为输出 XML 中的规范的元素名称。  如果编译器没有找到 `member`，它会发出警告。  
  
 将名称括在单引号或双引号中。  
  
 有关如何创建对泛型类型的 cref 引用的信息，请参阅 [\<see>](../ide/see-visual-cpp.md)。  
  
 `description`  
 描述。  
  
## <a name="remarks"></a>备注  
 使用 [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。  
  
 Visual C++ 编译器将尝试通过文档注释在一次处理中解决 cref 引用。  因此，如果使用 C++ 查找规则，编译器找不到符号，引用将被标记为未解析。 请参阅 [\<seealso>](../ide/seealso-visual-cpp.md)，获取详细信息。  
  
## <a name="example"></a>示例  
  
```  
// xml_exception_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_exception_tag.dll  
using namespace System;  
  
/// Text for class EClass.  
public ref class EClass : public Exception {  
   // class definition ...  
};  
  
/// <exception cref="System.Exception">Thrown when... .</exception>  
public ref class TestClass {  
   void Test() {  
      try {  
      }  
      catch(EClass^) {  
      }  
   }  
};  
```  
  
## <a name="see-also"></a>请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)