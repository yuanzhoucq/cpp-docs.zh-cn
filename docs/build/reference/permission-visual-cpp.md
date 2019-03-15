---
title: '&lt;权限 > （c + + 文档注释）'
ms.date: 11/04/2016
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C++ XML tag
- permission C++ XML tag
ms.assetid: 537ee2bc-95bd-48e4-9ce6-3420c3da87f4
ms.openlocfilehash: 764048f7bc579afa6862bdff40968588955dc307
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824905"
---
# <a name="ltpermissiongt"></a>&lt;permission&gt;

使用 \<permission> 可以记录成员访问权限 借助 <xref:System.Security.PermissionSet>，可以指定对成员的访问权限。

## <a name="syntax"></a>语法

```
<permission cref="member">description</permission>
```

#### <a name="parameters"></a>参数

*member*<br/>
对可从当前编译环境调用的成员或字段的引用。 编译器检查是否存在给定的代码元素，并将 `member` 转换为输出 XML 中规范的元素名称。  将名称括在单引号或双引号中。

如果编译器没有找到 `member`，它会发出警告。

有关如何创建对泛型类型的 cref 引用的信息，请参阅 [\<see>](see-visual-cpp.md)。

*description*<br/>
对成员访问权限的说明。

## <a name="remarks"></a>备注

使用 [/doc](doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。

MSVC 编译器将尝试解析在一次传递通过文档注释的 cref 引用。  因此，如果使用 C++ 查找规则，编译器找不到符号，引用将被标记为未解析。 请参阅 [\<seealso>](seealso-visual-cpp.md)，获取详细信息。

## <a name="example"></a>示例

```
// xml_permission_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_permission_tag.dll
using namespace System;
/// Text for class TestClass.
public ref class TestClass {
   /// <permission cref="System::Security::PermissionSet">Everyone can access this method.</permission>
   void Test() {}
};
```

## <a name="see-also"></a>请参阅

[XML 文档](xml-documentation-visual-cpp.md)
