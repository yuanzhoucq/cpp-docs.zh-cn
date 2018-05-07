---
title: '&lt;包括&gt;（Visual c + +） |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- include
- <include>
dev_langs:
- C++
helpviewer_keywords:
- include C++ XML tag
- <include> C++ XML tag
ms.assetid: 392a3e61-0371-4617-8362-446650876ce3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b4c1a75acb89d9510dd7f489e5d0d582611da8de
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="ltincludegt-visual-c"></a>&lt;包括&gt;（Visual c + +）
通过 \<include> 标记，可在其他文件中引用描述源代码中类型和成员的注释。 这是对直接在源代码文件中放入文档注释的替代方法。  例如，你可以使用\<包括 > 将在整个团队或公司的标准"样本"注释插入。  
  
## <a name="syntax"></a>语法  
  
```  
<include file='filename' path='tagpath' />  
```  
  
#### <a name="parameters"></a>参数  
 `filename`  
 包含文档的文件的名称。 可使用路径来限定文件名。  将名称括在单引号或双引号中。  如果编译器没有找到 `filename`，它会发出警告。  
  
 `tagpath`  
 一个有效的 XPath 表达式选择文件中包含所需的节点集。  
  
 `name`  
 标记中的名称说明符（位于注释之前）；`name` 将有 `id`。  
  
 `id`  
 标记的 ID（位于注释之前）。  将名称括在单引号或双引号中。  
  
## <a name="remarks"></a>备注  
 \<include> 标记使用 XML XPath 语法。 请参阅有关如何自定义使用 XPath 文档\<包括 >。  
  
 使用 [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。  
  
## <a name="example"></a>示例  
 这是多文件示例。 第一个文件，使用\<包括 >，包含以下的文档注释：  
  
```  
// xml_include_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_include_tag.dll  
  
/// <include file='xml_include_tag.doc' path='MyDocs/MyMembers[@name="test"]/*' />  
public ref class Test {  
   void TestMethod() {  
   }  
};  
  
/// <include file='xml_include_tag.doc' path='MyDocs/MyMembers[@name="test2"]/*' />  
public ref class Test2 {  
   void Test() {  
   }  
};  
```  
  
 第二个文件是 xml_include_tag.doc，包含下列文档注释：  
  
```  
<MyDocs>  
  
<MyMembers name="test">  
<summary>  
The summary for this type.  
</summary>  
</MyMembers>  
  
<MyMembers name="test2">  
<summary>  
The summary for this other type.  
</summary>  
</MyMembers>  
  
</MyDocs>  
```  
  
## <a name="program-output"></a>程序输出  
  
```  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>t2</name>  
    </assembly>  
    <members>  
        <member name="T:Test">  
            <summary>  
The summary for this type.  
</summary>  
        </member>  
        <member name="T:Test2">  
            <summary>  
The summary for this other type.  
</summary>  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="see-also"></a>请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)