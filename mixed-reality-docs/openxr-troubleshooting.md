---
title: 對 OpenXR 進行疑難排解
description: 針對 OpenXR 應用程式中的問題進行疑難排解。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、原生、原生應用程式、自訂引擎、中介軟體、疑難排解
ms.openlocfilehash: 269982596ed6162d9c2f1ec999a446bcecd6ba2a
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83228003"
---
# <a name="openxr-troubleshooting"></a>對 OpenXR 進行疑難排解

以下是使用 Windows Mixed Reality OpenXR 執行時間開發 OpenXR 應用程式時的一些疑難排解秘訣。  如果您有任何關於<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 規格</a>的其他問題，請造訪<a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR 論壇</a>或<a href="https://khr.io/slack" target="_blank">#openxr 頻道的時差</a>。

>[!NOTE]
>在目前的 Windows Mixed Reality OpenXR 執行時間中，有 x86 應用程式的已知問題。  您目前應該建立適用于 x64 的桌面 OpenXR 應用程式。

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>OpenXR 應用程式未啟動 Windows Mixed Reality

如果您的 OpenXR 應用程式在執行時未啟動 Windows Mixed Reality，則 Windows Mixed Reality OpenXR 執行時間可能不會設定為作用中的執行時間。  請務必遵循上述指示，以[開始使用適用于 Windows Mixed Reality 耳機的 OpenXR](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) ，讓執行時間變成作用中。

您也可以執行[Windows Mixed Reality OpenXR 開發人員工具](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools)，以取得有關系統上的 Windows Mixed Reality OpenXR 執行時間狀態的其他疑難排解協助。

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a>混合現實入口網站未顯示 [設定 OpenXR] 功能表項目

請確定您至少執行 Windows 10 2018 年10月更新（1809）。  如果您是在舊版的 Windows 10 上，您可以使用[Windows 10 更新](https://www.microsoft.com//software-download/windows10)小幫手升級至5月2019更新（1903）。

如果您有較舊版本的混合現實入口網站應用程式，則可能無法使用 [設定 OpenXR] 功能表項目。  檢查是否有[混合現實入口網站應用程式更新](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m)，以確保您擁有最新版本。

請注意，如果 Windows Mixed Reality OpenXR 執行時間已安裝且作用中，就不會顯示 [設定 OpenXR] 功能表項目。  您可以安裝[Windows Mixed Reality OpenXR 開發人員工具](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools)，以判斷系統上 OpenXR 執行時間的目前狀態。