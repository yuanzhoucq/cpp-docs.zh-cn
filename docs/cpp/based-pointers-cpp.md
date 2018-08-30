---
title: 基于指针 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __based
- __based_cpp
dev_langs:
- C++
helpviewer_keywords:
- __based keyword [C++]
- based pointers
- pointers, based
ms.assetid: 1e5f2e96-c52e-4738-8e14-87278681205e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: afecaafc5a9d3c1eb9a9466cce303a493d355ce0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196202"
---
# <a name="based-pointers-c"></a>基指针 (C++)
**Microsoft 专用**  
  
 **__Based**关键字可以声明基于指针 （是从现有指针的偏移量的指针） 的指针。  
  
## <a name="syntax"></a>语法  
  
```  
  
type __based( base ) declarator   
```  
  
## <a name="remarks"></a>备注  
 基于指针地址的指针是唯一的形式 **__based**关键字在 32 位或 64 位编译中有效。 对于 Microsoft 32 位 C/C++ 编译器，基指针是相对于 32 位指针基的 32 位偏移量。 一个针对 64 位环境的类似限制保留，其中基指针是相对于 64 位基的 64 位偏移量。  
  
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
>  此外可以通过实现保留包含指针的标识符[内存映射文件](/windows/desktop/Memory/file-mapping)。  
  
 当取消对基指针的引用时，必须显式指定基或通过声明隐式公开基。  
  
 与以前版本的兼容性 **_based**是的同义词 **__based**。  
  
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
  
## <a name="see-also"></a>请参阅  
 [关键字](../cpp/keywords-cpp.md)   
 [alloc_text](../preprocessor/alloc-text.md)