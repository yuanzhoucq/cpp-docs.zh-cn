---
title: 链接器工具错误 LNK2033
ms.date: 11/04/2016
f1_keywords:
- LNK2033
helpviewer_keywords:
- LNK2033
ms.assetid: d61db467-9328-4788-bf54-e2a20537f13f
ms.openlocfilehash: 7e95823e23215848ff3e5d201171523c9009eb2d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298901"
---
# <a name="linker-tools-error-lnk2033"></a>链接器工具错误 LNK2033

type 的未解析的 typeref 标记 （令牌）

一种类型在 MSIL 元数据中没有一个定义。

使用编译时，会发生 LNK2033 **/clr: safe**和没有前向声明的 MSIL 模块，该类型中的 MSIL 模块的引用位置中的类型。

需要下定义类型 **/clr: safe**。

有关详细信息，请参阅 [/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>示例

下面的示例生成 LNK2033。

```
// LNK2033.cpp
// compile with: /clr:safe
// LNK2033 expected
ref class A;
ref class B {};

int main() {
   A ^ aa = nullptr;
   B ^ bb = nullptr;   // OK
};
```