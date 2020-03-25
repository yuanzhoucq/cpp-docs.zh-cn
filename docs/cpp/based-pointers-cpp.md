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
ms.openlocfilehash: f16e9f6582ae846c0c19fc1dcbd86f09baba713e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181390"
---
# <a name="based-pointers-c"></a>基指针 (C++)

**__Based**关键字允许你根据指针（作为来自现有指针的偏移量的指针）声明指针。 **__Based**关键字是 Microsoft 特定的。

## <a name="syntax"></a>语法

```
type __based( base ) declarator
```

## <a name="remarks"></a>备注

基于指针地址的指针是在32位或64位编译中唯一有效的 **__based**关键字形式。 对于 Microsoft 32 位 C/C++ 编译器，基指针是相对于 32 位指针基的 32 位偏移量。 一个针对 64 位环境的类似限制保留，其中基指针是相对于 64 位基的 64 位偏移量。

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
>  还可以通过使用[内存映射文件](/windows/win32/Memory/file-mapping)来保存包含指针的标识符。

当取消对基指针的引用时，必须显式指定基或通过声明隐式公开基。

为了与早期版本兼容， **_based**是 **__based**的同义词，除非指定编译器选项[/za \(禁用语言扩展）](../build/reference/za-ze-disable-language-extensions.md) 。

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

[关键字](../cpp/keywords-cpp.md)<br/>
[alloc_text](../preprocessor/alloc-text.md)
