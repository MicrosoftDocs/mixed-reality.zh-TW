---
title: 更新 Windows Mixed Reality 的應用程式 SteamVR
description: 更新 SteamVR 應用程式來充分發揮 Windows Mixed Reality 耳機與相容性的最佳做法。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR，相容性
ms.openlocfilehash: db21651df8e586edf500f0d05def4b1ea5474284
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591189"
---
# <a name="updating-your-steamvr-application-for-windows-mixed-reality"></a>更新 Windows Mixed Reality 的應用程式 SteamVR

我們鼓勵開發人員測試和最佳化 Windows Mixed Reality 耳機上執行其 SteamVR 體驗。 這份文件涵蓋了一般開發人員可以對確保他們的體驗 Windows Mixed reality 執行絕佳的增強功能。

## <a name="initial-setup-instructions"></a>初始安裝指示

若要開始測試您的遊戲或應用程式上 Windows Mixed Reality 確定到第一個遵循我們[入門指南。](http://aka.ms/WindowsMixedRealitySteamVR)

## <a name="controller-models"></a>控制器模型
1. 如果您的應用程式呈現控制器模型：
    * 使用[Windows Mixed Reality 動作控制器模型](motion-controllers.md#rendering-the-motion-controller-model)
    * 若要取得本機使用 IVRRenderModel::GetComponentState 將轉換為元件組件 （例如。 指標姿勢）
2. 體驗有法線慣用手的概念，應從輸入 Api 來區分控制器取得提示[（Unity 範例）](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)

## <a name="controls"></a>控制項

在設計或調整您的控制項配置請記住下列保留的命令組：
1. 按一下向下**左邊和右邊類比搖桿**保留供**Steam 儀表板**。
2. **Windows 按鈕**一律會傳回使用者家用的 Windows Mixed Reality。

可能的話，thumb 隨身碟的預設基礎來比對的屏障[Windows Mixed Reality 家用](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)屏障行為

## <a name="tooltips-and-ui"></a>工具提示和 UI

許多的 VR 遊戲善用動作控制器的工具提示並教導使用者他們的遊戲或應用程式的最重要命令的覆疊。 微調您的應用程式的 Windows Mixed reality 時建議您檢閱您的體驗，並確定將對應至 Windows 控制器模型的工具提示的這個部分。

另外有您的經驗顯示控制站的映像的位置中的任何點請務必提供更新的映像使用 Windows Mixed Reality 動作控制站。

## <a name="haptics"></a>Haptics

開頭[Windows 10 April 2018 Update](release-notes-april-2018.md)，haptics 現在支援以 SteamVR 體驗 Windows Mixed reality。 如果 SteamVR 應用程式或遊戲已經包含 haptics 的支援，其應該正常運作 （進行任何其他的工作） 與[Windows Mixed Reality 動作控制器](motion-controllers.md)。

Windows Mixed Reality 動作控制站會使用標準 haptics 馬達，而不是線性的傳動器，在某些其他 SteamVR 動作控制站，而可能會導致稍微不同高於預期的使用者體驗中找到。 因此，我們建議測試及調整您的 haptics 設計，含有 Windows Mixed Reality 動作控制站。 比方說，有時簡短 haptic 跳動 （5-10 毫秒） 是 Windows Mixed Reality 動作控制站上較不明顯。 若要產生更明顯的 pulse，試驗傳送長 「 按一下 」 (40 70ms) 來提供馬達的更多時間才能啟動之前被告知電源一次。

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>從 Windows Mixed Reality 開始 功能表啟動 SteamVR 應用程式

透過資料流所散發的 VR 體驗，我們已[SteamVR beta 版更新 Windows Mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800)以及最新[Windows 測試人員](https://insider.windows.com)RS5 航班以便 SteamVR 標題會出現在混合實境 [開始] 功能表中 [所有應用程式 」 會自動列出。 與安裝這些軟體版本，您的客戶現在可以啟動 SteamVR 項目直接從家用的 Windows Mixed Reality 內而不需移除其耳機。

## <a name="windows-mixed-reality-logo"></a>Windows Mixed Reality 標誌

若要顯示標題的 Windows Mixed Reality 支援，請前往 「 編輯存放區頁面 」 連結，應用程式登陸頁面上，按一下 [基本資訊] 索引標籤上，捲動到 「 虛擬實境。 」 取消核取 「 隱藏 Windows Mixed Reality"，然後發佈到市集。

## <a name="bugs-and-feedback"></a>Bug 和意見反應

改善 Windows Mixed Reality SteamVR 體驗時，您的意見非常寶貴。 請提交的所有意見反應和透過 bug [Windows 意見反應中樞](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback)。 以下是一些[如何讓您 SteamVR 的意見反應盡可能為有用的秘訣](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)。

如果您有問題或意見，若要共用，您也可以連線到我們在我們[Steam 論壇](http://steamcommunity.com/app/719950/discussions/)。

## <a name="faqs-and-troubleshooting"></a>常見問題和疑難排解

如果您執行一般的問題，設定或播放您的經驗[查看最新疑難排解步驟](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)。

## <a name="see-also"></a>另請參閱
* [安裝工具](install-the-tools.md)
* [耳機式和移動控制器的驅動程式記錄](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Windows Mixed Reality 最小電腦的硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
