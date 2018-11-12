---
title: '&lt;returns&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- returns C++ XML tag
- <returns> C++ XML tag
ms.assetid: 5e3b0ed9-838d-4953-a93e-76d2d0a19fb9
ms.openlocfilehash: 2ed21b1a7b0bca12185e054b3b5452e0bf04d4d7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494505"
---
# <a name="ltreturnsgt-visual-c"></a>&lt;returns&gt; (Visual C++)

在方法声明的注释中应使用 \<returns> 标记来描述返回值。

## <a name="syntax"></a>语法

```
<returns>description</returns>
```

#### <a name="parameters"></a>参数

description<br/>
返回值的说明。

## <a name="remarks"></a>备注

使用 [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。

## <a name="example"></a>示例

```
// xml_returns_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_returns_tag.dll

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <returns>Returns zero.</returns>
   int GetZero() { return 0; }
};
```

## <a name="see-also"></a>请参阅

[XML 文档](../ide/xml-documentation-visual-cpp.md)