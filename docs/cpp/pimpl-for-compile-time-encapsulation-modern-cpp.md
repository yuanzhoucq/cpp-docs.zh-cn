---
title: "用于编译时 （现代 c + +） 封装的 Pimpl |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6a109015f3d30b04eaf89e769e1265c49663599f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="pimpl-for-compile-time-encapsulation-modern-c"></a>用于编译时封装的 Pimpl（现代 C++）
*Pimpl 惯用语法*现代的 c + + 技术，可隐藏实现，以便最大程度减少耦合，从而单独的接口。 Pimpl 是短的"指向的实现。" 你已可能熟悉的概念，但是知道它通过类似 Cheshire Cat 或编译器防火墙惯用语法其他名称。  
  
## <a name="why-use-pimpl"></a>为何使用 pimpl？  
 下面是 pimpl 惯用语法可以如何改进软件开发生命周期：  
  
-   编译依赖项的最小化。  
  
-   接口和实现分离。  
  
-   可移植性。  
  
## <a name="pimpl-header"></a>Pimpl 标头  
  
```cpp  
// my_class.h  
class my_class {  
   //  ... all public and protected stuff goes here ...  
private:  
   class impl; unique_ptr<impl> pimpl; // opaque type here  
};  
  
```  
  
 重新生成级联和脆弱对象布局，可避免 pimpl 惯用语法。 它非常适合 （间接） 常用类型。  
  
## <a name="pimpl-implementation"></a>Pimpl 实现  
 定义`impl`.cpp 文件中的类。  
  
```cpp  
// my_class.cpp  
class my_class::impl {  // defined privately here  
  // ... all private data and functions: all of these  
  //     can now change without recompiling callers ...  
};  
my_class::my_class(): pimpl( new impl )  
{  
  // ... set impl values ...   
}  
```  
  
## <a name="best-practices"></a>最佳做法  
 考虑是否添加对非引发交换专用化的支持。  
  
## <a name="see-also"></a>请参阅  
 [欢迎回到 c + +](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C + + 语言参考](../cpp/cpp-language-reference.md)   
 [C++ 标准库](../standard-library/cpp-standard-library-reference.md)