---
title: '&lt;value&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- value
- <value>
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
ms.openlocfilehash: 84a19c96e3e7024dbb891c6bde91646d4731b2be
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599285"
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