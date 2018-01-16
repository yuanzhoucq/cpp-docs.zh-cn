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
ms.workload: cplusplus
ms.openlocfilehash: 3795f289a454503e80aa06d281543cd94aaa0a55
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
 在类别 [ 异常 ](../standard-library/exception-class.md) 中由 `what` 返回的值由 `_Message` 和 [error_code](../standard-library/error-code-class.md)（`code`或`error_code(_Errval, _Errcat)`）的存储对象构成。  
  
 成员函数 `code` 返回存储的 [error_code](../standard-library/error-code-class.md) 对象。  
  
## <a name="requirements"></a>惠?  
 **标头：** \<system_error>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [<system_error>](../standard-library/system-error.md)

