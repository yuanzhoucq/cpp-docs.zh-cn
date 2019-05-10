---
title: 编译器错误 C3809
ms.date: 11/04/2016
f1_keywords:
- C3809
helpviewer_keywords:
- C3809
ms.assetid: 37eca584-c20c-464e-8e45-a987214b7ce4
ms.openlocfilehash: 5ff57050980ddb770ea2fcfa4d0be4f42f5ee834
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391889"
---
# <a name="compiler-error-c3809"></a>编译器错误 C3809

“class”: 托管或 WinRT 类型不能有任何友元函数/类/接口

托管类型和 Windows 运行时类型不允许使用友元。 若要修复此错误，请不要声明在托管或 Windows 运行时类型内声明友元。

下面的示例生成 C3809：

```
// C3809a.cpp
// compile with: /clr
ref class A {};

ref class B
{
public:
   friend ref class A;   // C3809
};

int main()
{
}
```