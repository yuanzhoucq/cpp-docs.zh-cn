---
title: 编译器错误 C3836
ms.date: 11/04/2016
f1_keywords:
- C3836
helpviewer_keywords:
- C3836
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
ms.openlocfilehash: 33860273db07894a9a4d15ba6d578598a18819ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208052"
---
# <a name="compiler-error-c3836"></a>编译器错误 C3836

静态构造函数不能有成员初始值设定项列表

托管的类不能具有静态构造函数还具有成员初始化列表。 公共语言运行时类初始化，初始化静态数据成员调用静态类构造函数。

## <a name="example"></a>示例

下面的示例生成 C3836:

```
// C3836a.cpp
// compile with: /clr
ref class M
{
   static int s_i;

public:
   static M() :  s_i(1234)   // C3836, delete initializer to resolve
   {
   }
};

int main()
{
}
```
