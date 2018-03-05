---
title: "SAL 批注 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- __z annotation
- ref annotation
- _opt annotation
- __checkreturn annotatioin
- __deref_opt annotation
- deref_opt annotation
- __deref annotation
- __in annotation
- annotations [C++]
- z annotation
- _inout annotation
- __ref annotation
- full annotation
- _in annotation
- _ref annotation
- __out annotation
- _ecount annotation
- SAL annotations
- __opt annotation
- inout annotation
- in annotation
- _CA_SHOULD_CHECK_RETURN
- __bcount annotation
- _full annotation
- _bcount annotation
- deref annotation
- part annotation
- _out annotation
- __nz annotation
- __part annotation
- opt annotation
- __full annotation
- _nz annotation
- _z annotation
- out annotation
- __ecount annotation
- __inout annotation
- SAL annotations, _CA_SHOULD_CHECK_RETURN
- _deref_opt annotation
- _deref annotation
- nz annotation
- _part annotation
- ecount annotation
- bcount annotation
ms.assetid: 81893638-010c-41a0-9cb3-666fe360f3e0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 79e10e9b93beb811f42e15574014df6a464aadb3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="sal-annotations"></a>SAL 批注
如果检查库的标头文件，您可能会注意一些特殊的注释，例如，`_In_z` 和 `_Out_z_cap_(_Size)`。 这些是 Microsoft 源代码注释语言 (SAL) 的示例。SAL 提供一组描述函数如何使用其参数的注释，例如，它关于参数的假设以及关于完成的保证。 标头文件 \<sal.h> 定义了这些注释。  
  
 有关在 Visual Studio 中使用 SAL 注释的详细信息，请参阅[使用 SAL 注释减少 C/C++ 代码缺陷](/visualstudio/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects)。  
  
## <a name="see-also"></a>请参阅  
 [CRT 库功能](../c-runtime-library/crt-library-features.md)