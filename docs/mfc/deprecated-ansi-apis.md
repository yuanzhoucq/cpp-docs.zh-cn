---
title: "弃用的 ANSI API | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC, ANSI 已弃用方法"
ms.assetid: c7c5a6fd-95e4-4bee-b3d5-d3826c30947d
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# 弃用的 ANSI API
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft 基础类 \(MFC\) \(MFC\) 库迁移在根据 Unicode 字符集的类和方法。  因此，多个 ANSI 版本 MFC 方法已弃用。  将来使用这些方法应用程序代码成为 Unicode 版本。  
  
 启动使用 Windows 公共控件版本 6.1，在 [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)]附带下，ANSI 方法。  
  
## CButton 类  
  
```  
AFX_ANSI_DEPRECATED BOOL GetIdealSize(LPSIZE psize) const;  
AFX_ANSI_DEPRECATED BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist) const;  
AFX_ANSI_DEPRECATED BOOL GetTextMargin(LPRECT pmargin) const;  
AFX_ANSI_DEPRECATED BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);  
AFX_ANSI_DEPRECATED BOOL SetTextMargin(LPRECT pmargin);  
```  
  
## CComboBoxEx 类  
  
```  
AFX_ANSI_DEPRECATED HRESULT SetWindowTheme(LPCWSTR pszSubAppName);  
```  
  
## CEdit 类  
  
```  
AFX_ANSI_DEPRECATED BOOL GetCueBanner(LPWSTR lpszText, int cchText) const;  
AFX_ANSI_DEPRECATED BOOL SetCueBanner(LPCWSTR lpszText, BOOL fDrawIfFocused = FALSE);  
```  
  
## CLinkCtrl 类  
 整个类已弃用。  
  
## 类 CListCtrl  
  
```  
AFX_ANSI_DEPRECATED void CancelEditLabel();  
AFX_ANSI_DEPRECATED int EnableGroupView(BOOL fEnable);  
AFX_ANSI_DEPRECATED int GetGroupInfo(int iGroupId, PLVGROUP pgrp) const;  
AFX_ANSI_DEPRECATED void GetGroupMetrics(PLVGROUPMETRICS pGroupMetrics) const;  
AFX_ANSI_DEPRECATED BOOL GetInsertMark(LPLVINSERTMARK lvim) const;  
AFX_ANSI_DEPRECATED COLORREF GetInsertMarkColor() const;  
AFX_ANSI_DEPRECATED int GetInsertMarkRect(LPRECT pRect) const;  
AFX_ANSI_DEPRECATED COLORREF GetOutlineColor() const;  
AFX_ANSI_DEPRECATED UINT GetSelectedColumn() const;  
AFX_ANSI_DEPRECATED BOOL GetTileInfo(PLVTILEINFO pti) const;  
AFX_ANSI_DEPRECATED BOOL GetTileViewInfo(PLVTILEVIEWINFO ptvi) const;  
AFX_ANSI_DEPRECATED DWORD GetView() const;  
AFX_ANSI_DEPRECATED BOOL HasGroup(int iGroupId) const;  
AFX_ANSI_DEPRECATED int InsertGroup(int index, PLVGROUP pgrp);  
AFX_ANSI_DEPRECATED void InsertGroupSorted(PLVINSERTGROUPSORTED pStructInsert);  
AFX_ANSI_DEPRECATED int InsertMarkHitTest(LPPOINT pPoint, LPLVINSERTMARK lvim) const;  
AFX_ANSI_DEPRECATED BOOL IsGroupViewEnabled() const;  
AFX_ANSI_DEPRECATED void MoveGroup(int iGroupId, int toIndex);  
AFX_ANSI_DEPRECATED void MoveItemToGroup(int idItemFrom, int idGroupTo);  
AFX_ANSI_DEPRECATED void RemoveAllGroups();  
AFX_ANSI_DEPRECATED int RemoveGroup(int iGroupId);  
AFX_ANSI_DEPRECATED BOOL SetGroupInfo(int iGroupId, PLVGROUP pGroup);  
AFX_ANSI_DEPRECATED void SetGroupMetrics(PLVGROUPMETRICS pGroupMetrics);  
AFX_ANSI_DEPRECATED BOOL SetInfoTip(PLVSETINFOTIP plvInfoTip);  
AFX_ANSI_DEPRECATED BOOL SetInsertMark(LPLVINSERTMARK lvim);  
AFX_ANSI_DEPRECATED COLORREF SetInsertMarkColor(COLORREF color);  
AFX_ANSI_DEPRECATED COLORREF SetOutlineColor(COLORREF color);  
AFX_ANSI_DEPRECATED void SetSelectedColumn(int iCol);  
AFX_ANSI_DEPRECATED BOOL SetTileInfo(PLVTILEINFO pti);  
AFX_ANSI_DEPRECATED BOOL SetTileViewInfo(PLVTILEVIEWINFO ptvi);  
AFX_ANSI_DEPRECATED DWORD SetView(int iView);  
AFX_ANSI_DEPRECATED BOOL SortGroups(PFNLVGROUPCOMPARE _pfnGroupCompare, LPVOID _plv);  
```  
  
## CReBarCtrl 类  
  
```  
AFX_ANSI_DEPRECATED void GetBandMargins(PMARGINS pMargins) const;  
AFX_ANSI_DEPRECATED HRESULT SetWindowTheme(LPCWSTR pszSubAppName);  
```  
  
## CToolBarCtrl 类  
  
```  
AFX_ANSI_DEPRECATED void GetMetrics(LPTBMETRICS ptbm) const;  
AFX_ANSI_DEPRECATED void SetMetrics(LPTBMETRICS ptbm);  
AFX_ANSI_DEPRECATED HRESULT SetWindowTheme(LPCWSTR pszSubAppName);  
```  
  
## CToolTipCtrl 类  
  
```  
AFX_ANSI_DEPRECATED HRESULT SetWindowTheme(LPCWSTR pszSubAppName);  
```  
  
## 请参阅  
 [Windows Vista 公共控件的生成要求](../mfc/build-requirements-for-windows-vista-common-controls.md)