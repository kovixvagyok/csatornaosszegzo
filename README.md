# MI EZ?

🇭🇺 [Magyar](#magyar) · 🇬🇧 [English](#english)



---

## Magyar

Készítettem Claude barátommal egy frankó kis weboldalt, ahol láthatod az **ÖSSZES** csatornád statisztikáját, akár egybevonva. Olyan, mint a YouTube Studio, csak nem kell átlépegetni a fiókokba.

# **Az oldal nem tárol adatot.** 

Az adatok közvetlenül a böngésződ és a Google (YouTube) között mozognak, nincs köztes szerver. A bejelentkezési adatok és a letöltött statisztikák csak a saját böngésződben, a munkamenet idejére maradnak meg, a beállításaid (pl. a bevétel elrejtése) pedig a böngésző helyi tárolójában.

> ⚠️ **FONTOS: az egész projekt AI-al készült és teljesen vibe-kódolt.** - szükségem volt egy oldalra, ahol láthatom az összes csatornám analitikáját, ezért létrehoztam magamnak, mert nem akartam erre pénzt kiszórni. Nem nézte át profi fejlesztő, vagy biztonsági szakember és ha emiatt ellopják a csatornádat akkor bocsi. (valszeg akkor az enyémet is lol) de ennek elvileg nem kéne megtörténnie, mert semmi adatot nem rögzít az oldal a szerverre.

### Mit tud
- Több csatorna statját tudod nézni összesítve és csatornánként is.
- Megtekintések, watch time, feliratkozások *(ez nem pontos)* és bevétel (Forintban). Mindegyikhez van grafikon, napi-havi lebontással. 
- Felosztás: 7 / 28 / 90 / 365 nap, ALL TIME vagy dátumintervallum
- Kattintható kártyák, amikre a felső grafikon átáll
- Kilistázza a  videókat, shortsokat és élő adásokat külön oszlopban, legfrissebtől, vagy legnézettebbtől *(a premierek valamiért élő adásnál jelennek meg, valamint a rövid hosszú videók shortsnál, ez módosítható)*
- Bevétel elrejtése/megjelenítése gomb

### Használat
Az oldal a Google bejelentkezést használja, és csak a saját csatornáidhoz fér hozzá, **olvasási jogosultsággal**.

Ha nem a készítő fiókjával használod, **saját Google Cloud OAuth Client ID kell** hozzá:

1. A [Google Cloud Console](https://console.cloud.google.com)-ban hozz létre egy projektet, és kapcsold be a **YouTube Data API v3** és a **YouTube Analytics API** szolgáltatást.
2. A **Google Auth Platform** menüben állítsd be a hozzájárulási képernyőt (External), és add hozzá magad **teszt felhasználóként** (Audience).
3. A **Clients** menüben hozz létre egy **Web application** típusú klienst. Az **Authorized JavaScript origins** közé írd be az oldal címét útvonal és záró perjel nélkül (pl. `https://kovixvagyok.github.io`).
4. Nyisd meg az oldalt, kattints a **Client ID** gombra, illeszd be az azonosítót, majd kattints a **Csatorna csatlakoztatása** gombra. Minden csatornát külön kell csatlakoztatni (a Google ablakban az adott csatornát válaszd ki).

Helyi kipróbáláshoz: `python3 -m http.server 8000`, majd `http://localhost:8000/index.html` (az `http://localhost:8000` eredetet is add hozzá a klienshez).

### Korlátok
- A YouTube API a **feliratkozószámot 3 értékes jegyre kerekíti**, ezért az érték eltérhet a Studióban látottól.
- A **valós idejű** (percenkénti) Studio-panel nem érhető el az API-n keresztül.
- A napi adatok általában 1–3 nap késéssel érkeznek.
- A short, a premier és az élő adás szétválasztását az API nem támogatja pontosan, ezért a besorolás becslés, kézzel javítható.
- A bejelentkezési token kb. 1 óráig érvényes, utána újra kell csatlakoztatni a csatornát.

Ez egy nem hivatalos, független projekt. Nem áll kapcsolatban a Google-lal vagy a YouTube-bal.

---

## English

I built a neat little website with my buddy Claude where you can see the stats of **ALL** your channels, even combined. It's like YouTube Studio, but you don't have to switch between accounts.

# **The site doesn't store any data.**

Data moves directly between your browser and Google (YouTube), with no middleman server. Your sign-in details and the downloaded stats stay only in your own browser for the duration of the session, and your settings (e.g. hiding revenue) are kept in the browser's local storage.

> ⚠️ **IMPORTANT: this whole project was made with AI and is fully vibe-coded.** - I needed a page where I could see the analytics of all my channels, so I made one for myself because I didn't want to spend money on it. It hasn't been reviewed by a professional developer or a security expert, and if your channel gets stolen because of it, sorry (it'd probably mean mine got stolen too lol). That shouldn't happen though, since the site doesn't save any data to a server.

### Features
- View the stats of multiple channels combined or per channel.
- Views, watch time, subscribers *(not exact)* and revenue (in HUF). Each has its own chart, with daily or monthly breakdown.
- Time range: 7 / 28 / 90 / 365 days, ALL TIME, or a custom date range
- Clickable cards that switch the top chart to that channel
- Lists your videos, Shorts and live streams in separate columns, sorted by newest or most viewed *(premieres show up under live streams for some reason, and short regular videos show up under Shorts. This can be fixed manually)*
- Button to hide/show revenue

### Usage
The site uses Google sign-in and only accesses your own channels, with **read-only permission**.

If you're not using it with the author's account, you need **your own Google Cloud OAuth Client ID**:

1. In the [Google Cloud Console](https://console.cloud.google.com), create a project and enable the **YouTube Data API v3** and the **YouTube Analytics API**.
2. In the **Google Auth Platform** menu, set up the consent screen (External) and add yourself as a **test user** (Audience).
3. In the **Clients** menu, create a **Web application** client. Under **Authorized JavaScript origins**, enter the site's address without a path or trailing slash (e.g. `https://kovixvagyok.github.io`).
4. Open the site, click the **Client ID** button, paste your ID, then click **Csatorna csatlakoztatása** (Connect channel). Each channel has to be connected separately (select the given channel in the Google popup).

To try it locally: `python3 -m http.server 8000`, then open `http://localhost:8000/index.html` (also add the `http://localhost:8000` origin to your client).

### Limitations
- The YouTube API **rounds the subscriber count to 3 significant digits**, so the value may differ from what you see in Studio.
- The **real-time** (per-minute) Studio panel isn't available through the API.
- Daily data usually arrives with a 1–3 day delay.
- The API can't accurately tell Shorts, premieres and live streams apart, so the classification is an estimate and can be corrected manually.
- The sign-in token is valid for about 1 hour, after which you need to reconnect the channel.

This is an unofficial, independent project. It is not affiliated with Google or YouTube.
