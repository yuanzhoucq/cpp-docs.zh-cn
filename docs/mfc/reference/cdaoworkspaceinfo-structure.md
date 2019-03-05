---
title: CDaoWorkspaceInfo 结构
ms.date: 11/04/2016
f1_keywords:
- CDaoWorkspaceInfo
helpviewer_keywords:
- CDaoWorkspaceInfo structure [MFC]
- DAO (Data Access Objects), Workspaces collection
ms.assetid: a1f4b25e-f9c6-4196-b075-d1df99c54124
ms.openlocfilehash: afbc73c079a6deec3f3e1b7455f9f2dbface5025
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271549"
---
# <a name="cdaoworkspaceinfo-structure"></a>CDaoWorkspaceInfo 结构

`CDaoWorkspaceInfo`结构包含有关为数据访问对象 (DAO) 数据库访问定义的工作区的信息。

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

*m_strName*<br/>
唯一地命名工作区对象。 若要直接检索此属性的值，请调用 querydef 对象[GetName](../../mfc/reference/cdaoquerydef-class.md#getname)成员函数。 有关详细信息，请参阅主题 DAO 帮助中的"名称属性"。

*m_strUserName*<br/>
一个值，表示工作区对象的所有者。 有关相关信息，请参阅主题 DAO 帮助中的"用户名属性"。

*m_bIsolateODBCTrans*<br/>
一个值，指示是否涉及同一个 ODBC 数据库的多个事务之间隔离。 有关详细信息，请参阅[CDaoWorkspace::SetIsolateODBCTrans](../../mfc/reference/cdaoworkspace-class.md#setisolateodbctrans)。 有关相关信息，请参阅主题 DAO 帮助中的"IsolateODBCTrans 属性"。

## <a name="remarks"></a>备注

在工作区是类的对象[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)。 对主要、 次要和上面所有的引用指示如何通过返回的信息[GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo)类中的成员函数`CDaoWorkspace`。

检索的信息[CDaoWorkspace::GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo)成员函数存储在`CDaoWorkspaceInfo`结构。 `CDaoWorkspaceInfo` 此外定义了`Dump`成员函数在调试生成。 可以使用`Dump`转储的内容`CDaoWorkspaceInfo`对象。

## <a name="requirements"></a>要求

**标头：** afxdao.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoWorkspace 类](../../mfc/reference/cdaoworkspace-class.md)
