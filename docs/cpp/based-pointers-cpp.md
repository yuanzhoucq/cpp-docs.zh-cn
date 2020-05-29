---
title: 基指针 (C++)
ms.date: 10/09/2018
f1_keywords:
- __based
- _based
- __based_cpp
helpviewer_keywords:
- __based keyword [C++]
- based pointers
- pointers, based
ms.assetid: 1e5f2e96-c52e-4738-8e14-87278681205e
ms.openlocfilehash: 24c3a7f85c4ea05c38f3ab1d3f637ea0ab24d4c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363749"
---
# <a name="based-pointers-c"></a>基指针 (C++)

**__based**关键字允许您根据指针（与现有指针偏移的指针）声明指针。 **__based**关键字特定于 Microsoft。

## <a name="syntax"></a>语法

```
type __based( base ) declarator
```

## <a name="remarks"></a>备注

基于指针地址的指针是 **__based**关键字的唯一形式，在 32 位或 64 位编译中有效。 对于 Microsoft 32 位 C/C++ 编译器，基指针是相对于 32 位指针基的 32 位偏移量。 一个针对 64 位环境的类似限制保留，其中基指针是相对于 64 位基的 64 位偏移量。

基于指针的指针的用途之一是用于包含指针的永久标识符。 可将包含基于指针的指针的链接列表保存到磁盘，然后重新加载到内存中的另一个位置，并且指针保持有效。 例如：

```cpp
// based_pointers1.cpp
// compile with: /c
void *vpBuffer;
struct llist_t {
   void __based( vpBuffer ) *vpData;
   struct llist_t __based( vpBuffer ) *llNext;
};
```

将指针 `vpBuffer` 分配给程序中后面某个时间点分配的内存地址。 相对于 `vpBuffer` 的值重新定位链接的列表。

> [!NOTE]
> 包含指针的持久标识符也可以通过使用[内存映射文件](/windows/win32/Memory/file-mapping)来完成。

当取消对基指针的引用时，必须显式指定基或通过声明隐式公开基。

为了与早期版本兼容，**除非**指定编译器选项[/Za\(禁用语言扩展，](../build/reference/za-ze-disable-language-extensions.md)否则_based是 **__based**的同义词。

## <a name="example"></a>示例

下面的代码演示了通过更改其基来更改基指针。

```cpp
// based_pointers2.cpp
// compile with: /EHsc
#include <iostream>

int a1[] = { 1,2,3 };
int a2[] = { 10,11,12 };
int *pBased;

typedef int __based(pBased) * pBasedPtr;

using namespace std;
int main() {
   pBased = &a1[0];
   pBasedPtr pb = 0;

   cout << *pb << endl;
   cout << *(pb+1) << endl;

   pBased = &a2[0];

   cout << *pb << endl;
   cout << *(pb+1) << endl;
}
```

```Output
1
2
10
11
```

## <a name="see-also"></a>另请参阅

[Keywords](../cpp/keywords-cpp.md)<br/>
[alloc_text](../preprocessor/alloc-text.md)
