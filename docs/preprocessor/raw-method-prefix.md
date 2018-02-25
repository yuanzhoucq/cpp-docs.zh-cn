---
title: "raw_method_prefix |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- raw_method_prefix
dev_langs:
- C++
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dc80d1468d3ac33bf7506aab98945b9c2e610e51
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="rawmethodprefix"></a>raw_method_prefix
**C + + 专用**  
  
 指定不同的前缀以避免名称冲突。  
  
## <a name="syntax"></a>语法  
  
```  
raw_method_prefix("Prefix")  
```  
  
#### <a name="parameters"></a>参数  
 `Prefix`  
 要使用的前缀。  
  
## <a name="remarks"></a>备注  
 低级属性和方法公开的成员函数使用的默认前缀名为**raw_**以避免与高级错误处理成员函数的名称冲突。  
  
> [!NOTE]
>  效果`raw_method_prefix`属性将不会更改通过的存在[raw_interfaces_only](#_predir_raw_interfaces_only)属性。 指定前缀时，`raw_method_prefix` 始终优先于 `raw_interfaces_only`。 如果同一 `#import` 语句中同时使用了这两个特性，则使用 `raw_method_prefix` 特性指定的前缀。  
  
 **结束 c + + 专用**  
  
## <a name="see-also"></a>请参阅  
 [#import 属性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指令](../preprocessor/hash-import-directive-cpp.md)