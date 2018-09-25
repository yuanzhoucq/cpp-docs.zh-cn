---
title: '&lt;value&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- value
- <value>
dev_langs:
- C++
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0a194e45fd79ae59dc91abb21a9fb038d3ec4008
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041683"
---
# <a name="ltvaluegt-visual-c"></a>&lt;value&gt; (Visual C++)
借助 \<value>标记，可以描述属性和属性访问器方法。 请注意，在 Visual Studio 集成开发环境中使用代码向导添加属性时，将为新属性添加 [\<summary>](../ide/summary-visual-cpp.md)标记。 然后，应手动添加 \<value> 标记，描述属性表示的值。  
  
## <a name="syntax"></a>语法  
  
```  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a>参数  
*property-description*<br/>
属性的说明。  
  
## <a name="remarks"></a>备注  
 使用 [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。  
  
## <a name="example"></a>示例  
  
```  
// xml_value_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_value_tag.dll  
using namespace System;  
/// Text for class Employee.  
public ref class Employee {  
private:  
   String ^ name;  
   /// <value>Name accesses the value of the name data member</value>  
public:  
   property String ^ Name {  
      String ^ get() {  
         return name;   
      }  
      void set(String ^ i) {  
         name = i;  
      }  
   }  
};  
```  
  
## <a name="see-also"></a>请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)