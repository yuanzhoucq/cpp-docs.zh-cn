---
title: "CDaoErrorInfo 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoErrorInfo structure [MFC]
- DAO (Data Access Objects), Errors collection
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: da47b4b68a9fd73b3962254121006eff47282336
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdaoerrorinfo-structure"></a>CDaoErrorInfo 结构
`CDaoErrorInfo`结构包含有关为数据访问对象 (DAO) 定义的错误对象信息。  
  
## <a name="syntax"></a>语法  
  
```  
struct CDaoErrorInfo  
{  
    long m_lErrorCode;  
    CString m_strSource;  
    CString m_strDescription;  
    CString m_strHelpFile;  
    long m_lHelpContext;  
};  
```  
  
#### <a name="parameters"></a>参数  
 *m_lErrorCode*  
 数值的 DAO 错误代码。 请参阅主题"可捕获中的数据访问错误"DAO 帮助。  
  
 *m_strSource*  
 对象或最初生成错误的应用程序的名称。 源属性指定一个字符串表达式，表示最初生成错误; 的对象表达式通常是对象的类名称。 有关详细信息，请参阅主题 DAO 帮助中的"源属性"。  
  
 *m_strDescription*  
 与错误关联的描述性字符串。 有关详细信息，请参阅主题 DAO 帮助中的"Description 属性"。  
  
 *m_strHelpFile*  
 Microsoft Windows 帮助文件的完全限定的路径。 有关详细信息，请参阅 DAO 帮助中的主题"HelpContext，HelpFile 属性"。  
  
 *m_lHelpContext*  
 Microsoft Windows 帮助文件中的主题上下文 ID。 有关详细信息，请参阅 DAO 帮助中的主题"HelpContext，HelpFile 属性"。  
  
## <a name="remarks"></a>备注  
 MFC 不封装 DAO 类中的错误对象。 相反， [CDaoException](../../mfc/reference/cdaoexception-class.md)类提供了用于访问在 DAO 中包含的错误集合的接口**数据库引擎**对象，还包含所有工作区的对象。 当 MFC DAO 操作引发`CDaoException`对象，需捕获，MFC 将填充`CDaoErrorInfo`结构并将它存储在异常对象的[m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo)成员。 (如果你选择直接调用 DAO，则必须调用异常对象的[GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo)成员函数自己以填充`m_pErrorInfo`。)  
  
 有关处理 DAO 错误的详细信息，请参阅文章[异常： 数据库异常](../../mfc/exceptions-database-exceptions.md)。 有关相关信息，请参阅主题 DAO 帮助中的"错误对象"。  
  
 检索的信息[CDaoException::GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo)成员函数将存储在`CDaoErrorInfo`结构。 检查[m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo)中的数据成员`CDaoException`捕获异常处理程序或调用中的对象`GetErrorInfo`从`CDaoException`显式创建以检查可能有的错误的对象直接调用 DAO 接口过程中出现。 `CDaoErrorInfo`此外定义`Dump`成员函数在调试生成。 你可以使用`Dump`以转储的内容`CDaoErrorInfo`对象。  
  
## <a name="requirements"></a>惠?  
 **标头：** afxdao.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoException 类](../../mfc/reference/cdaoexception-class.md)
