---
title: "&lt;fstream&gt; | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <fstream>
dev_langs:
- C++
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e479caecbca33a19854f6800a037eb093d0b2f5a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="ltfstreamgt"></a>&lt;fstream&gt;
定义若干类，这些类支持在存储于外部文件中的序列上的 iostreams 操作。  
  
## <a name="syntax"></a>语法  
  
```  
#include <fstream>  
  
```  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|专用于 `char` 模板参数的类型 `basic_filebuf`。|  
|[fstream](../standard-library/fstream-typedefs.md#fstream)|专用于 `char` 模板参数的类型 `basic_fstream`。|  
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|专用于 `char` 模板参数的类型 `basic_ifstream`。|  
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|专用于 `char` 模板参数的类型 `basic_ofstream`。|  
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|专用于 `wchar_t` 模板参数的类型 `basic_fstream`。|  
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|专用于 `wchar_t` 模板参数的类型 `basic_ifstream`。|  
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|专用于 `wchar_t` 模板参数的类型 `basic_ofstream`。|  
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|专用于 `wchar_t` 模板参数的类型 `basic_filebuf`。|  
  
### <a name="classes"></a>类  
  
|||  
|-|-|  
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|该模板类描述对 **Elem** 类型的元素（其字符特征由类 **Tr** 确定）与外部文件中存储的元素序列之间的来回传输进行控制的流缓冲区。|  
|[basic_fstream](../standard-library/basic-fstream-class.md)|该模板类描述一个对象，该对象使用 [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**> 类的流缓冲区控制元素和编码对象的插入和提取，具有 **Elem** 类型的元素，其字符特征由 **Tr** 类确定。|  
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|该模板类描述一个对象，该对象控制从 [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**> 类的流缓冲区提取元素和编码对象，具有 **Elem** 类型的元素，其字符特征由 **Tr** 类确定。|  
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|该模板类描述一个对象，该对象控制向 [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**> 类的流缓冲区插入元素和编码对象，具有 **Elem** 类型的元素，其字符特征由 **Tr** 类确定。|  
  
## <a name="see-also"></a>请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)



