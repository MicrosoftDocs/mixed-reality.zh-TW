---
title: 使用 Unity 和 Visual Studio 的最佳作法
description: 秘訣與技巧，來簡化使用 Unity 和 Visual Studio 中建立的混合的實境應用程式的工作流程。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: visual studio 中，HoloLens，沈浸式耳機，unity，部署
ms.openlocfilehash: 80a533851b3bee0d747a90dfececbaa558c4ec1f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596686"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>使用 Unity 和 Visual Studio 的最佳作法

使用 Unity 建立混合的實境應用程式開發人員必須 Unity 和 Visual Studio 來建置應用程式套件部署到 HoloLens 和/或沈浸式耳機之間切換。 根據預設的 Visual Studio 的兩個執行個體都需要 （一個修改 Unity 指令碼），另一個来部署到裝置和偵錯。 下列程序允許使用單一的 Visual Studio 執行個體的開發、 減少匯出 Unity 專案的頻率和改善的偵錯體驗。

## <a name="improving-iteration-time"></a>改善的反覆項目時間

常見的工作流程問題時使用 Unity 和 Visual Studio 有多個視窗開啟的 Visual Studio 和需要不斷切換來逐一查看的 Visual Studio 和 Unity。
1. **Unity** -修改場景和匯出的 Visual Studio 方案
2. **Visual Studio (1)** -適用於修改指令碼
3. **Visual Studio (2)** -針對建置和部署 Unity 到裝置中匯出的 Visual Studio 方案

幸運的是，還有以簡化的 Visual Studio 的單一執行個體，並減少經常匯出從 Unity 的方法。

當[匯出您的專案，從 Unity](exporting-and-building-a-unity-visual-studio-solution.md)，檢查**UnityC#專案**[檔案 > 建置設定] 功能表中的核取方塊。 現在，您匯出從 Unity 專案會包含您的專案的所有C#指令碼，並有幾項優點：
* 使用 Visual Studio 的相同執行個體，用來撰寫指令碼和建置/部署您的專案
* 匯出從 Unity 場景變更在 Unity Editor; 時，才變更指令碼的內容可以在 Visual Studio 中完成而不重新匯出。

具有**UnityC#專案**啟用，只有一個執行個體的每個程式需要開啟：
1. **Unity** -修改場景和匯出的 Visual Studio 方案
2. **Visual Studio** -修改指令碼，然後建置和部署 Unity 到裝置中匯出的 Visual Studio 方案

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity

下載[Visual Studio Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)

**Visual Studio Tools for Unity 的優點**
* 偵錯 Unity 編輯器中的 play 模式，從 Visual Studio 中放置中斷點，評估變數和複雜運算式。
* 找不到您的指令碼完全相同的階層，會顯示 Unity 使用 Unity Project Explorer。
* 取得直接在 Visual Studio 的 Unity 主控台。
* 使用精靈來快速建立，或瀏覽至 指令碼。

## <a name="expose-c-class-variables-for-easy-tuning"></a>公開 （expose)C#類別用來微調簡單的變數

有兩種方式來公開類別變數。 若要這樣做的建議的方式是將 [SerializeField] 屬性加入至您的私用變數。 這可讓他們存取從編輯器，但未以程式設計方式公開。  另一個選項是對C#類別的變數公開 」 以在編輯器 UI 中公開它們。 

這兩種方法可使您能夠輕鬆地調整同時播放編輯器中的變數。 這是用來微調互動 mechanic 屬性特別有用。

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Windows SDK 或 Unity 在升級後，重新產生 UWP 的 Visual Studio 方案

簽入原始檔控制的 UWP 的 Visual Studio 解決方案可以取得升級至新的 Windows SDK 或 Unity 引擎之後過期。 您可以解決此問題在升級之後從 Unity 建置新的 UWP 方案，然後將差異合併到簽入的解決方案。

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>使用文字格式的資產，以便比較的內容變更

以文字格式儲存的資產，讓您更輕鬆地檢閱在 Visual Studio 中的內容變更差異比對。 您可以啟用 [編輯 > 專案設定 > 編輯器] 中變更**資產序列化**模式**強制文字**。 不過，合併變更文字的資產檔案很容易發生錯誤，而且不建議使用，因此請考慮啟用二進位的獨佔簽出原始檔控制系統中。
