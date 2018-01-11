---
title: "CUserTool 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CUserTool
- AFXUSERTOOL/CUserTool
- AFXUSERTOOL/CUserTool::CopyIconToClipboard
- AFXUSERTOOL/CUserTool::DrawToolIcon
- AFXUSERTOOL/CUserTool::GetCommand
- AFXUSERTOOL/CUserTool::GetCommandId
- AFXUSERTOOL/CUserTool::Invoke
- AFXUSERTOOL/CUserTool::Serialize
- AFXUSERTOOL/CUserTool::SetCommand
- AFXUSERTOOL/CUserTool::SetToolIcon
- AFXUSERTOOL/CUserTool::LoadDefaultIcon
- AFXUSERTOOL/CUserTool::m_strArguments
- AFXUSERTOOL/CUserTool::m_strInitialDirectory
- AFXUSERTOOL/CUserTool::m_strLabel
dev_langs: C++
helpviewer_keywords:
- CUserTool [MFC], CopyIconToClipboard
- CUserTool [MFC], DrawToolIcon
- CUserTool [MFC], GetCommand
- CUserTool [MFC], GetCommandId
- CUserTool [MFC], Invoke
- CUserTool [MFC], Serialize
- CUserTool [MFC], SetCommand
- CUserTool [MFC], SetToolIcon
- CUserTool [MFC], LoadDefaultIcon
- CUserTool [MFC], m_strArguments
- CUserTool [MFC], m_strInitialDirectory
- CUserTool [MFC], m_strLabel
ms.assetid: 7c287d3e-d012-488d-b4e1-aa0f83f294bb
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 38600b2e6eac6ad181baf1263d9e4d10295732b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cusertool-class"></a>CUserTool 类
用户工具是运行外部应用程序的菜单项。 **工具**选项卡**自定义**对话框 ( [CMFCToolBarsCustomizeDialog 类](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)) 允许用户添加用户工具，并指定名称、 命令、 自变量，并每个用户工具的的初始目录。  
  
## <a name="syntax"></a>语法  
  
```  
class CUserTool : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CUserTool::CopyIconToClipboard](#copyicontoclipboard)||  
|[CUserTool::DrawToolIcon](#drawtoolicon)|在指定的矩形中绘制用户工具图标。|  
|[CUserTool::GetCommand](#getcommand)|返回一个字符串，包含与用户工具关联的命令的文本。|  
|[CUserTool::GetCommandId](#getcommandid)|返回用户工具中的菜单项的命令 ID。|  
|[CUserTool::Invoke](#invoke)|执行与用户工具关联的命令。|  
|[CUserTool::Serialize](#serialize)|从存档读取该对象或将该对象写入存档。 （重写 [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)。）|  
|[CUserTool::SetCommand](#setcommand)|设置与用户工具关联的命令。|  
|[CUserTool::SetToolIcon](#settoolicon)|从使用工具关联的应用程序加载用户工具的图标。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CUserTool::LoadDefaultIcon](#loaddefaulticon)|加载用户工具的默认图标。|  
  
### <a name="data-members"></a>数据成员  
  
|name|描述|  
|----------|-----------------|  
|[CUserTool::m_strArguments](#m_strarguments)|用户工具命令行参数。|  
|[CUserTool::m_strInitialDirectory](#m_strinitialdirectory)|用户工具初始目录。|  
|[CUserTool::m_strLabel](#m_strlabel)|该工具的菜单项中显示的工具名称。|  
  
## <a name="remarks"></a>备注  
 有关如何启用应用程序中的用户工具的详细信息，请参阅[CUserToolsManager 类](../../mfc/reference/cusertoolsmanager-class.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何创建一个工具，来自`CUserToolsManager`对象，设置`m_strLabel`成员变量，并设置用户工具运行的应用程序。 此代码片段属于[Visual Studio 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CUserTool](../../mfc/reference/cusertool-class.md)  
  
## <a name="requirements"></a>惠?  
 **标头：** afxusertool.h  
  
##  <a name="copyicontoclipboard"></a>CUserTool::CopyIconToClipboard  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL CopyIconToClipboard();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="drawtoolicon"></a>CUserTool::DrawToolIcon  
 在指定的矩形的中心绘制用户工具图标。  
  
```  
void DrawToolIcon(
    CDC* pDC,  
    const CRect& rectImage);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rectImage`  
 指定要显示的图标区域的坐标。  
  
##  <a name="getcommand"></a>CUserTool::GetCommand  
 返回一个字符串，包含与用户工具关联的命令的文本。  
  
```  
const CString& GetCommand() const;  
```  
  
### <a name="return-value"></a>返回值  
 对引用`CString`对象，其中包含与用户工具关联的命令的文本。  
  
##  <a name="getcommandid"></a>CUserTool::GetCommandId  
 返回用户工具的命令 ID。  
  
```  
UINT GetCommandId() const;  
```  
  
### <a name="return-value"></a>返回值  
 此用户工具命令 ID。  
  
##  <a name="invoke"></a>CUserTool::Invoke  
 执行与用户工具关联的命令。  
  
```  
virtual BOOL Invoke();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则执行了该命令则不为否则为 0。  
  
### <a name="remarks"></a>备注  
 调用[ShellExecute](http://msdn.microsoft.com/library/windows/desktop/bb762153)执行与用户工具关联的命令。 如果该命令为空或者失败的函数[ShellExecute](http://msdn.microsoft.com/library/windows/desktop/bb762153)失败。  
  
##  <a name="loaddefaulticon"></a>CUserTool::LoadDefaultIcon  
 加载用户工具的默认图标。  
  
```  
virtual HICON LoadDefaultIcon();
```  
  
### <a name="return-value"></a>返回值  
 加载图标的句柄 ( `HICON`)，或`NULL`有无法加载默认图标。  
  
### <a name="remarks"></a>备注  
 无法从该工具的可执行文件加载用户定义的工具的图标时，框架将调用此方法。  
  
 重写此方法以提供您自己的默认工具图标。  
  
##  <a name="m_strarguments"></a>CUserTool::m_strArguments  
 用户工具命令行参数。  
  
```  
CString m_strArguments;  
```  
  
### <a name="remarks"></a>备注  
 在调用时，将此字符串传递给该工具[CUserTool::Invoke](#invoke)或当用户单击与此工具关联的命令。  
  
##  <a name="m_strinitialdirectory"></a>CUserTool::m_strInitialDirectory  
 指定用户工具的初始目录。  
  
```  
CString m_strInitialDirectory;  
```  
  
### <a name="remarks"></a>备注  
 此变量指定在调用时，该工具中执行的初始目录[CUserTool::Invoke](#invoke)或当用户单击与此工具关联的命令。  
  
##  <a name="m_strlabel"></a>CUserTool::m_strLabel  
 显示在工具菜单项的标签。  
  
```  
CString m_strLabel;  
```  
  
##  <a name="serialize"></a>CUserTool::Serialize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>参数  
 [in] `ar`  
  
### <a name="remarks"></a>备注  
  
##  <a name="setcommand"></a>CUserTool::SetCommand  
 设置用户工具运行的应用程序。  
  
```  
void SetCommand(LPCTSTR lpszCmd);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszCmd`  
 指定新的应用程序要与用户工具相关联。  
  
### <a name="remarks"></a>备注  
 调用此方法以设置新运行的应用程序的用户工具。 该方法销毁旧图标，并从该给定应用程序加载新建图标。 如果它无法从应用程序加载一个图标，它将加载用户工具的默认图标通过调用[CUserTool::LoadDefaultIcon](#loaddefaulticon)。  
  
##  <a name="settoolicon"></a>CUserTool::SetToolIcon  
 从该工具使用的应用程序加载用户工具的图标。  
  
```  
virtual HICON SetToolIcon();
```  
  
### <a name="return-value"></a>返回值  
 加载图标句柄。  
  
### <a name="remarks"></a>备注  
 调用此方法以加载该菜单项上显示的图标。 此方法搜索该工具使用的可执行文件中的图标。 如果它没有默认图标，图标是由[CUserTool::LoadDefaultIcon](#loaddefaulticon)改为使用。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx 类](../../mfc/reference/cwinappex-class.md)   
 [CUserToolsManager 类](../../mfc/reference/cusertoolsmanager-class.md)
