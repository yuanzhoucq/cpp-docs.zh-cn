---
title: '&lt;摘要 > (C++文档注释)'
ms.date: 11/04/2016
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C++ XML tag
- summary C++ XML tag
ms.assetid: cdeeefbb-1339-45d6-9002-10042a9a2726
ms.openlocfilehash: 68bb8b7c269b3406438e5cf21dde7179f7e67646
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318181"
---
# <a name="ltsummarygt"></a>&lt;summary&gt;

\<summary> 标记应当用于描述类型或类型成员。 使用 [\<remarks>](remarks-visual-cpp.md) 可针对某个类型说明添加补充信息。

## <a name="syntax"></a>语法

```
<summary>description</summary>
```

#### <a name="parameters"></a>参数

*description*<br/>
对象的摘要。

## <a name="remarks"></a>备注

\<summary> 标记的文本是 IntelliSense 中类型相关信息的唯一源，它也在[对象浏览器](/visualstudio/ide/viewing-the-structure-of-code)和代码注释 Web 报表中显示。

使用 [/doc](doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。

## <a name="example"></a>示例

```
// xml_summary_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_summary_tag.dll

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <summary>MyMethod is a method in the MyClass class.
   /// <para>Here's how you could make a second paragraph in a description. <see cref="System::Console::WriteLine"/> for information about output statements.</para>
   /// <seealso cref="MyClass::MyMethod2"/>
   /// </summary>
   void MyMethod(int Int1) {}

   /// text
   void MyMethod2() {}
};
```

## <a name="see-also"></a>请参阅

[XML 文档](xml-documentation-visual-cpp.md)
