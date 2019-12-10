---
title: '&lt;备注 > （C++文档注释）'
ms.date: 11/04/2016
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- <remarks> C++ XML tag
- remarks C++ XML tag
ms.assetid: c820083b-3192-40ab-9ec8-1472c55b4247
ms.openlocfilehash: 096280526b12feff33377a705f7c03548a1f0f13
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988660"
---
# <a name="ltremarksgt"></a>&lt;remarks&gt;

\<remarks> 标记用于添加有关某个类型的信息，从而补充由 [\<summary>](summary-visual-cpp.md) 指定的信息。 此信息显示在[对象浏览器](/visualstudio/ide/viewing-the-structure-of-code)和代码注释 Web 报表中。

## <a name="syntax"></a>语法

```
<remarks>description</remarks>
```

#### <a name="parameters"></a>参数

description<br/>
对成员的说明。

## <a name="remarks"></a>备注

使用 [/doc](doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。

## <a name="example"></a>示例

```cpp
// xml_remarks_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_remarks_tag.dll

using namespace System;

/// <summary>
/// You may have some primary information about this class.
/// </summary>
/// <remarks>
/// You may have some additional information about this class.
/// </remarks>
public ref class MyClass {};
```

## <a name="see-also"></a>另请参阅

[XML 文档](xml-documentation-visual-cpp.md)
