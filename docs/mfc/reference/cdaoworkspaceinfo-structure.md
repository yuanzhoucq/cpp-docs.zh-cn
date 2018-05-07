---
title: CDaoWorkspaceInfo 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoWorkspaceInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoWorkspaceInfo structure [MFC]
- DAO (Data Access Objects), Workspaces collection
ms.assetid: a1f4b25e-f9c6-4196-b075-d1df99c54124
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd6979124916e8a9cc1dc723008491bababc0322
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cdaoworkspaceinfo-structure"></a>CDaoWorkspaceInfo 结构
`CDaoWorkspaceInfo`结构包含有关定义为数据访问对象 (DAO) 数据库访问工作区的信息。  
  
## <a name="syntax"></a>语法  
  
```  
struct CDaoWorkspaceInfo  
{  
    CString m_strName;           // Primary  
    CString m_strUserName;       // Secondary  
    BOOL m_bIsolateODBCTrans;    // All  
};  
```  
  
#### <a name="parameters"></a>参数  
 `m_strName`  
 唯一命名的工作区对象。 若要直接检索此属性的值，调用 querydef 对象[GetName](../../mfc/reference/cdaoquerydef-class.md#getname)成员函数。 有关详细信息，请参阅主题 DAO 帮助中的"名称属性"。  
  
 *m_strUserName*  
 一个值，表示工作区中对象的所有者。 有关相关信息，请参阅主题 DAO 帮助中的"用户名属性"。  
  
 *m_bIsolateODBCTrans*  
 一个值，该值指示是否隔离，则涉及相同的 ODBC 数据库的多个事务。 有关详细信息，请参阅[CDaoWorkspace::SetIsolateODBCTrans](../../mfc/reference/cdaoworkspace-class.md#setisolateodbctrans)。 有关相关信息，请参阅主题 DAO 帮助中的"IsolateODBCTrans 属性"。  
  
## <a name="remarks"></a>备注  
 工作区是类的对象[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)。 对主、 辅助数据库，以及所有上面的引用指示如何通过返回的信息[GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo)类中的成员函数`CDaoWorkspace`。  
  
 检索的信息[CDaoWorkspace::GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo)成员函数将存储在`CDaoWorkspaceInfo`结构。 `CDaoWorkspaceInfo` 此外定义`Dump`成员函数在调试生成。 你可以使用`Dump`以转储的内容`CDaoWorkspaceInfo`对象。  
  
## <a name="requirements"></a>要求  
 **标头：** afxdao.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoWorkspace 类](../../mfc/reference/cdaoworkspace-class.md)
