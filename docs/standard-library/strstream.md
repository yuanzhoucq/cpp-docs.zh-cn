---
title: '&lt;strstream&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <strstream>
dev_langs: C++
helpviewer_keywords: strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 91e127c30b8e360295d7451aa4b35ca8bd420e52
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ltstrstreamgt"></a>&lt;strstream&gt;
定义支持存储于 `char` 对象的分配数组中的序列上的 iostreams 操作的几个类。 这类序列可轻松地转换为 C 字符串或者从 C 字符串进行转换。  
  
## <a name="syntax"></a>语法  
  
```  
#include <strstream>  
  
```  
  
## <a name="remarks"></a>备注  
 类型 `strstream` 的对象使用作为 C 字符串的 `char` *。 使用 [\<sstream>](../standard-library/sstream.md)，以使用类型 [basic_string](../standard-library/basic-string-class.md) 的对象。  
  
> [!NOTE]
>  `<strstream>` 中的类已弃用。 请考虑转而使用 `<sstream>` 中的类。  
  
### <a name="classes"></a>类  
  
|||  
|-|-|  
|[strstreambuf 类](../standard-library/strstreambuf-class.md)|此类描述了一种流缓冲区，它对向存储在 `char` 数组对象中的元素序列传输元素和从该序列传输出元素进行控制。|  
|[istrstream 类](../standard-library/istrstream-class.md)|此类描述了一种对象，该对象可控制从 [strstreambuf](../standard-library/strstreambuf-class.md) 类的流缓冲区提取元素和编码对象。|  
|[ostrstream 类](../standard-library/ostrstream-class.md)|此类描述了一种对象，该对象可控制在 [strstreambuf](../standard-library/strstreambuf-class.md) 类的流缓冲区中插入元素和编码对象。|  
|[strstream 类](../standard-library/strstream-class.md)|此类描述了一种对象，该对象使用 [strstreambuf](../standard-library/strstreambuf-class.md) 类的流缓冲区控制元素和编码对象的插入和提取。|  
  
## <a name="see-also"></a>请参阅  
 [\<strstream>](../standard-library/strstream.md)   
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)



