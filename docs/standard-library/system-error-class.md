---
title: "system_error 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: system_error/std::system_error
dev_langs: C++
helpviewer_keywords: system_error class
ms.assetid: 2eeaacbb-8a4a-4ad7-943a-997901a77f32
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 975fcf228191695e419df2b04bd5578e15924f6b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="systemerror-class"></a>system_error 类
表示为报告低级别系统错误而引发的所有异常的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class system_error : public runtime_error {  
public:  
    explicit system_error(error_code _Errcode,
    const string& _Message = "");

    system_error(error_code _Errcode,
    const char *_Message);

    system_error(error_code::value_type _Errval,  
    const error_category& _Errcat,
    const string& _Message);

    system_error(error_code::value_type _Errval,  
    const error_category& _Errcat,
    const char *_Message);
const error_code& code() const throw();
const error_code& code() const throw();

 };  
```  
  
## <a name="remarks"></a>备注  
 在类 [异常](../standard-library/exception-class.md) 中返回 `what` 的值是由 `_Message` 和 [error_code](../standard-library/error-code-class.md) 类型（`code`或`error_code(_Errval, _Errcat)`）的存储对象构成的。  
  
 成员函数 `code` 返回存储的 [error_code](../standard-library/error-code-class.md) 对象。  
  
## <a name="requirements"></a>要求  
 **标头：**\<system_error>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<system_error>](../standard-library/system-error.md)

