---
title: "文件常量 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _O_EXCL
- _O_RDWR
- _O_APPEND
- _O_RDONLY
- _O_TRUNC
- _O_CREAT
- _O_WRONLY
dev_langs:
- C++
helpviewer_keywords:
- _O_RDWR constant
- O_EXCL constant
- O_RDWR constant
- O_WRONLY constant
- O_APPEND constant
- O_CREAT constant
- _O_CREAT constant
- _O_APPEND constant
- _O_EXCL constant
- O_TRUNC constant
- _O_RDONLY constant
- _O_TRUNC constant
- O_RDONLY constant
- _O_WRONLY constant
ms.assetid: c8fa5548-9ac2-4217-801d-eb45e86f2fa4
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 354d107b9bbaf3f60153fbce5ee66b14e2a5b96d
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="file-constants"></a>文件常量
## <a name="syntax"></a>语法  
  
```  
  
#include <fcntl.h>  
  
```  
  
## <a name="remarks"></a>备注  
 由这些常量中的一个或多个常量构成的整数表达式确定允许进行的读取或写入操作的类型。 它是通过将一个或多个常量与平移模式常量组合来构成的。  
  
 文件常量如下所示：  
  
 `_O_APPEND`  
 在每次执行写入操作前，将文件指针重新定位到文件尾。  
  
 `_O_CREAT`  
 创建一个文件并打开该文件以进行写入；如果有由 filename 指定的文件存在，则此操作不起作用。  
  
 `_O_EXCL`  
 如果由 filename 指定的文件存在，则将返回一个错误值。 仅在与 `_O_CREAT` 一起使用时适用。  
  
 `_O_RDONLY`  
 打开文件以仅供读取；如果提供此标志，则无法提供 `_O_RDWR` 和 `_O_WRONLY`。  
  
 `_O_RDWR`  
 打开文件以供读取和写入；如果提供此标志，则无法提供 `_O_RDONLY` 和 `_O_WRONLY`。  
  
 `_O_TRUNC`  
 打开现有文件并将其截断为零长度；此文件必须具有写入权限。 销毁此文件的内容。 如果提供此标志，则无法指定 `_O_RDONLY`。  
  
 `_O_WRONLY`  
 打开文件以仅供写入；如果提供此标志，则无法提供 `_O_RDONLY` 和 `_O_RDWR`。  
  
## <a name="see-also"></a>另请参阅  
 [_open、_wopen](../c-runtime-library/reference/open-wopen.md)   
 [_sopen、_wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [全局常量](../c-runtime-library/global-constants.md)
