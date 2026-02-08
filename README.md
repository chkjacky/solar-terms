### ☀️ 24 Solar Terms
From the Earth's perspective, the Sun moves through a year across the stars or celestial sphere along a path known as the ecliptic, which is measured in 360 degrees longitude. 

The 24 solar terms divide the ecliptic into 24 equal segments, with 15 degrees of the Sun's longitude between the terms. 

Reference: [**Hong Kong Observatory**](https://www.weather.gov.hk/en/gts/time/24solarterms.htm)

### 👨‍🏫 Prelude
This project is not a solar-term calculator.
All solar-term dates and times are programmatically retrieved from the Hong Kong Observatory and then automatically compiled into an `.ics` calendar file.

This solar-term calendar includes only the traditional Chinese 24 solar terms.
It does not include any public holidays from the PRC, ROC, Hong Kong, or Macau.

All solar-term dates and times are referenced from the [**Hong Kong Observatory**](https://www.weather.gov.hk/) and strictly use Hong Kong Time (HKT / UTC+8).

Each entry displays both the Chinese name and the English name of the solar term, making it easier for users to study traditional Chinese calendrical knowledge.
The calendar event title also appends the exact HKT time when the solar term begins, for example:
```
冬至 Winter Solstice @ 04:50
```

### 🔧 How to Use
_As of February 8, 2026, the Hong Kong Observatory provides solar-term data only up to 2028._

**1. Download and Import `.ics` Files**

Download the `.ics` files for the desired year and import it directly into your calendar application.

**2. Subscribe via URL**

Copy the link below and paste it into your calendar app to subscribe and receive automatic updates.

2026: 
```
https://raw.githubusercontent.com/chkjacky/solar-terms/refs/heads/main/solar-terms-2026.ics
```

2027:
```
https://raw.githubusercontent.com/chkjacky/solar-terms/refs/heads/main/solar-terms-2027.ics
```

2028:
```
https://raw.githubusercontent.com/chkjacky/solar-terms/refs/heads/main/solar-terms-2028.ics
```

2026 - 2028:
```
https://raw.githubusercontent.com/chkjacky/solar-terms/refs/heads/main/solar-terms-2026-2028.ics
```

### 🔴 Problem
Most existing solar-term `.ics` files found on GitHub or public repositories define events using `;VALUE=DATE`, and many of them do not specify a time zone.

What `;VALUE=DATE` means
- `;VALUE=DATE` creates an all-day event with no specific time.
- Example:
```
DTEND;VALUE=DATE:20260204
```
- This represents an event that lasts from midnight to midnight in the user’s local time zone, not UTC.
- Calendar applications do not apply any UTC offset to all-day events.
- In practice, 20260204 simply means “the entire day of February 04” in whatever time zone the user is in.

### 🟠 Why the time zone matters?
This calendar is strictly based on **Hong Kong Time** (UTC+8).
If the time zone is omitted, users in Western or far East time zones may see:
- The wrong calendar date, or
- The solar term appearing one day early or late

As a result, omitting the time zone can cause solar terms to be displayed incorrectly outside East Asia, which defeats the astronomical accuracy of the calendar.

#### Explanation:
Solar terms are essentially the exact moment when the Sun reaches a specific ecliptic longitude.
They are global astronomical events, not determined by local calendar dates.

1. A solar term is an astronomical instant - the moment the Sun reaches a specific ecliptic longitude.
2. This moment is unique in Universal Time (UTC).
3. People in different time zones will see different local dates and times:
```
Hong Kong: 2026/02/04 04:02 (HKT)
New York: 2026/02/03 15:02 (EST)
```
4. Therefore, the “date” of a solar term is converted based on the local time zone, **and it does not necessarily fall on the same calendar day everywhere**.

### 🟢 Solution
To address the time zone issue, this `.ics` file explicitly includes the Hong Kong Time (HKT / UTC+8) time zone. When imported into a calendar application, the event time is automatically converted to the user’s local time, ensuring accurate and consistent results across regions.

Instead of being defined as an all-day event, each solar term is created as a time-specific event, reflecting the exact moment the solar term begins.
For example
```
Spring Commences (Lìchūn in Mandarin / laap6 ceon1 in Cantonese) occurs at 2026-02-04 04:02 HKT
```

A small adjustment is applied to the event duration logic:
- If a solar term begins between 00:00 and 23:55 HKT, the event ends on the same day at 23:59:59.
- If a solar term begins after 23:55 HKT, the event ends at 00:10:00 on the following day, preventing the event from having an excessively short duration.

#### Note
The end time of an event does not indicate the end of the solar term itself.
Each solar term lasts approximately 15 days, though the exact duration varies slightly from year to year due to changes in the Earth’s orbital speed.

In this calendar, the event duration is used only to represent the start of the solar term, so there is no need to extend the event to cover the full length of the solar term.

### 💡 Summary:
1. Solar terms are globally synchronized astronomical events
2. The calendar date depends on the local time zone
3. So when it’s February 4 in Hong Kong, it may still be February 3 in New York


### 🥚 Fun Fact - Balancing an Egg at Spring Commences
There is a popular saying that:
If you can balance an egg upright at the moment of Spring Commences, it will bring good luck for the year.

Many people believe that:
- Eggs are easier to balance on the Spring Commences
- This has something to do with cosmic balance, gravity, or the Earth’s axis

>In Cantonese, the word “egg” can also be pronounced as “ceon1”, written as 「膥」 or 「春」.
For example, 「雞膥」 or 「雞春」 are colloquial terms for “chicken egg”, sharing a similar pronunciation with the word “spring”.
>
>In addition, the Chinese character 「立」 literally means to stand, to establish, or to begin.
>
>As a result, Lìchūn / laap6 ceon1 (立春) not only marks the astronomical commence of spring, but through phonetic and semantic coincidence, it has also been popularly interpreted as “standing an egg”. This wordplay gave rise to the folk tradition known as balancing an egg at the Spring Commences, which carries both linguistic charm and symbolic meaning.

However, study shows that:
- Gravity does not change on the Start of Spring
- The Earth’s axis and celestial alignment do not make eggs easier to balance
- You can balance an egg on any day of the year

### ☀️ 二十四節氣
從地球觀測，太陽一年裡在恆星間或天球劃過的軌道稱為黃道，以 360 度黃經來量度。

二十四節氣正好把黃道分成二十四等份，即每個氣相差黃經 15 度。

參考: [**香港天文台**](https://www.weather.gov.hk/tc/gts/time/24solarterms.htm)

---

### 👨‍🏫 序言
本專案並非節氣計算器。
所有節氣的日期與時間皆是程式化地從香港天文台取得，並再自動編譯生成為 `.ics` 行事曆檔案。

此節氣日曆僅包含二十四節氣本身，
不包含中國大陸（PRC）、台灣（ROC）、香港或澳門的任何公眾假期。

所有節氣的日期與時間均參考自[**香港天文台**](https://www.weather.gov.hk/)，並統一使用香港時間（HKT / UTC+8）。

每一個節氣項目同時顯示中文名稱與英文名稱，方便使用者學習與研究中國傳統曆法知識。
此外，日曆標題中亦會標註該節氣在香港時間正式開始的時刻，例如：
```
冬至 Winter Solstice @ 04:50
```

### 🔧 使用方式
_截至 2026年2月8日，香港天文台僅提供至 2028 年的節氣資料。_

**1. 下載 `.ics` 檔案並匯入行事曆**

下載對應年份的 `.ics` 檔案，直接匯入你的行事曆應用程式即可。

**2. 訂閱 URL**

複製以下連結，貼到你的行事曆應用程式中進行訂閱，即可自動獲取節氣更新。
各年份連結：

2026: 
```
https://raw.githubusercontent.com/chkjacky/solar-terms/refs/heads/main/solar-terms-2026.ics
```

2027:
```
https://raw.githubusercontent.com/chkjacky/solar-terms/refs/heads/main/solar-terms-2027.ics
```

2028:
```
https://raw.githubusercontent.com/chkjacky/solar-terms/refs/heads/main/solar-terms-2028.ics
```

2026 - 2028:
```
https://raw.githubusercontent.com/chkjacky/solar-terms/refs/heads/main/solar-terms-2026-2028.ics
```

### 🔴 所在問題
目前 GitHub 或其他公開倉庫中的節氣 `.ics` 檔案，大多僅使用 `;VALUE=DATE` 來設定事件，且多數未指定時區。

`;VALUE=DATE` 的含義
- `;VALUE=DATE`代表的是全天事件，沒有具體的時分秒。
- 例如：
```
DTEND;VALUE=DATE:20260204
```
- 這表示該事件會被行事曆視為使用者本地時區的一整天（從當天 00:00到 23:59）。
- 行事曆應用程式不會對全天事件套用 UTC 時差。
- 實際上，20260204 只代表「使用者本地時區的 2月4日 整天」。

### 🟠 為何必須指定時區
本節氣日曆是**嚴格依據香港時間**（UTC+8）編制的。
若未標示時區，位於歐美等西方或遠東地區的使用者可能會遇到：
- 節氣日期顯示錯誤，或
- 節氣被提前或延後一天顯示

這會導致節氣在不同地區出現偏差，從而喪失節氣本應具備的天文準確性。

#### 詳細說明
節氣本質上是太陽到達黃經的瞬間，它是一個全球統一的天文事件，不是根據當地日期決定的。


1. 節氣時間是天文上的瞬間 → 太陽到達特定黃經角度。
2. 這個瞬間用**世界統一時間**（UTC）是唯一的。
3. 不同時區的人看到的「日期」會不同：
```
香港 2026/02/04 04:02 HKT
紐約 2026/02/03 15:02 EST
```
4. 所以節氣「日期」是相對於當地時區換算的，**不是每個地方都剛好是同一天**。

### 🟢 解決方案
為了解決時區問題，此 `.ics` 檔案已明確指定香港時間（HKT / UTC+8）。當導入行事曆應用程式時，系統會自動轉換為使用者所在地的時間，從而確保在不同地區都能顯示正確的節氣時間。

本日曆不再將節氣設定為全天事件，而是以具體時間事件呈現，準確標示每個節氣開始的實際時刻。
例如：
```
立春發生於 2026年2月4日 04:02（香港時間）
```

在事件結束時間的處理邏輯上，做了些微調整：
若節氣發生於 00:00 至 23:55（香港時間）之間，事件結束時間設為當日 23:59:59。
若節氣發生於 23:55 之後，事件則延續至翌日 00:10:00，以避免事件時間過短。

#### 注意
事件的結束時間並不代表節氣本身的結束。
每個節氣實際上會持續約15天左右，但由於地球公轉速度的細微差異，每年的實際長度會略有不同。

在此日曆中，事件時間僅用於標示節氣的開始時刻，因此無需將事件時間設定為整個節氣的實際持續期間。

### 💡 總結
1. 節氣是全球同步的天文事件
2. 日期取決於當地時區
3. 所以香港的 2月4日，紐約可能還是 2月3日


### 🥚 有趣現象 - 立春立雞蛋
在立春這一天（或立春那一刻），民間流傳一個習俗：
只要在立春時把雞蛋立起來，就會帶來一整年的好運。

很多人也說：
- 立春這天雞蛋「特別容易立」
- 和天地陰陽平衡和地心引力有關

>在粵語中，「蛋」亦可讀作 「膥」或「春」（ceon1）。
>例如「雞膥」或「雞春」在口語中均指「雞蛋」，其讀音與「春」相近。
>
>此外，「立」在中文中本身就有 「站立」、「建立」、「開始」 之意。
>
>因此，「立春」除了表示節氣上春天的開始外，在語音與語義的巧合之下，亦被民間引申為 「立雞蛋」，形成了「立春立雞蛋」這個既具諧音趣味又富象徵意義的民俗說法。

研究已經表明：
- 地球引力在立春沒有特別變化
- 地軸或日月位置也不會讓雞蛋更容易站
- 任何一天或任何時間都可以把雞蛋立起來