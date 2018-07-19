---
title: 在库的内部修复依赖项 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- library internals in an upgraded Visual C++ project
- _Hash_seq in an upgraded Visual C++ project
ms.assetid: 493e0452-6ecb-4edc-ae20-b6fce2d7d3c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 148db60c7a3b1ae3f71269feec8024f6ff22a118
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839055"
---
# <a name="fix-your-dependencies-on-library-internals"></a>在库的内部修复依赖项

Microsoft 为标准库、绝大多数 C 运行时库和众多 Visual Studio 版本中的其他 Microsoft 库发布了源代码。 这一举措旨在帮助你了解库行为，并帮助调试代码。 发布库源代码的一个副作用是它会暴露某些内部值、数据结构和函数，即使它们并非库接口的一部分。 它们的名称通常以两道下划线开头，或一道下划线后跟一个大写字母，这种名字在 C++ 标准中予以保留并实现。 这些值、结构和函数是实现细节，有可能随时间过去、随库的发展而有所更改，因此我们强烈建议对它们不要有任何依赖项。 如果执意如此，则将存在代码不可移植的风险，并且在将代码迁移至新版本的库时，还有可能出现问题。  

在大多数情况下，每个 Visual Studio 版本的“新增功能”或“重大更改”文档都不会提到对库内部的更改。 毕竟你不应该被这些实现细节所影响。 但有时，在要使用某些代码时，可以看见库的内部是十分大的。 本主题讨论 CRT 上的依赖项，或可能用到的标准库内部，以及如何更新代码以删除这些依赖项，从而使其更富可移植性，或使其得以迁移至新版本的库。

## <a name="hashseq"></a>_Hash_seq  

在某些字符串类型上实现 `std::hash` 的内部哈希函数 `std::_Hash_seq(const unsigned char *, size_t)`，在最新版本的标准库中是可见的。 此函数在字符序列上实现了 [FNV-1a hash]( https://en.wikipedia.org/wiki/Fowler%E2%80%93Noll%E2%80%93Vo_hash_function)。  
  
删除此依赖项的方法有几种。  

-   如果要使用和 `basic_string` 相同的哈希代码机制将 `const char *` 序列加入无序的容器，则可利用使用 `std::string_view` 的 `std::hash` 模板重载，它将以可移植的方式返回哈希代码。 在未来，字符串库可能依赖（也可能不依赖） FNV-1a 哈希的使用，因此这是避免特定哈希算法上的依赖项的最佳方法。 
  
-   如果要通过任意内存生成 FNV-1a 哈希，则可使用 GitHub 上的 [VCSamples]( https://github.com/Microsoft/vcsamples) 存储库的独立头文件 - [fnv1a.hpp](https://github.com/Microsoft/VCSamples/tree/master/VC2015Samples/_Hash_seq)（在 [MIT license](https://github.com/Microsoft/VCSamples/blob/master/license.txt) 下）中的代码。 为方便起见，我们还在此处添加了副本。 可将此代码复制到头文件，将标头添加到任何受影响的代码，然后通过 `fnv1a_hash_bytes` 查找和替换 `_Hash_seq`。 你将在 `_Hash_seq` 中获得与内部实现相同的行为。 

```cpp  
/*
VCSamples
Copyright (c) Microsoft Corporation
All rights reserved. 
MIT License
Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED *AS IS*, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
*/
#include <stddef.h>

inline size_t fnv1a_hash_bytes(const unsigned char * first, size_t count) {
#if defined(_WIN64)
    static_assert(sizeof(size_t) == 8, "This code is for 64-bit size_t.");
    const size_t fnv_offset_basis = 14695981039346656037ULL;
    const size_t fnv_prime = 1099511628211ULL;

#else /* defined(_WIN64) */
    static_assert(sizeof(size_t) == 4, "This code is for 32-bit size_t.");
    const size_t fnv_offset_basis = 2166136261U;
    const size_t fnv_prime = 16777619U;
#endif /* defined(_WIN64) */

    size_t result = fnv_offset_basis;
    for (size_t next = 0; next < count; ++next)
        {   // fold in another byte
        result ^= (size_t)first[next];
        result *= fnv_prime;
        }
    return (result);
}
```  
  
## <a name="see-also"></a>请参阅  
  
[从 Visual C++ 早期版本升级项目](upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
[潜在的升级问题概述 (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)  
[将代码升级到通用 CRT](upgrade-your-code-to-the-universal-crt.md)  
