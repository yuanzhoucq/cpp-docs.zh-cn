---
title: '&lt;streambuf&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <streambuf>
dev_langs: C++
helpviewer_keywords: streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 19be7e9ce24003dd2c00ddb0f9d9a1f5e92a5363
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ltstreambufgt"></a>&lt;streambuf&gt;
包含 iostreams 标准标头 \<streambuf > 来定义此模板类 [basic_streambuf](../standard-library/basic-streambuf-class.md)，这是 iostreams 类的基本操作。 此标头通常包含在另一 iostream 标头中；很少会直接包含它。  
  
## <a name="syntax"></a>语法  
  
```  
#include <streambuf>  
  
```  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|专用化使用 `char` 作为模板参数的 `basic_streambuf`。|  
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|专用化使用 `wchar_t` 作为模板参数的 `basic_streambuf`。|  
  
### <a name="classes"></a>类  
  
|||  
|-|-|  
|[basic_streambuf 类](http://msdn.microsoft.com/en-us/d9c706ba-ce01-43e0-b0b2-a558fc53ea8d)|此模板类描述一个用于派生流缓冲区的抽象基类，该缓冲区控制元素与特定的流表示形式的来回传输。|  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)



