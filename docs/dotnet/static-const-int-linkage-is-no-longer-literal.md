---
title: 静态 Const Int 链接不再是文本 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- literal attribute [C++]
- constants, declaring
- integral constant expressions
ms.assetid: d2a5e3d2-ffb0-4b61-8114-bec5993a1195
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c51853274b061ba290ff90993f45ccdf3375349b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431289"
---
# <a name="static-const-int-linkage-is-no-longer-literal"></a>静态 Const Int 链接不再是文本的

声明常量成员的类已从托管扩展中的 c + + 更改为 Visual c + +。

尽管`static const`整型成员仍受支持，其链接属性已更改。 其以前的链接特性现在放置在整型成员。 例如，考虑下面的托管扩展类：

```
public __gc class Constants {
public:
   static const int LOG_DEBUG = 4;
};
```

这将生成以下字段 （请注意文本特性） 的基础 CIL 属性：

```
.field public static literal int32
modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier) STANDARD_CLIENT_PRX = int32(0x00000004)
```

尽管这仍在新语法会编译：

```
public ref class Constants {
public:
   static const int LOG_DEBUG = 4;
};
```

它不会再发出文本特性，并因此未被 CLR 运行时为常量：

```
.field public static int32 modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier) STANDARD_CLIENT_PRX = int32(0x00000004)
```

为了具有相同的语言间文本属性，该声明应更改为新的受支持`literal`，如下所示，数据成员

```
public ref class Constants {
public:
   literal int LOG_DEBUG = 4;
};
```

## <a name="see-also"></a>请参阅

[类或接口中的成员声明 (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[文本](../windows/literal-cpp-component-extensions.md)