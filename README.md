
# OSINT Tools Catalog

Переиспользуемая база open-source инструментов по поиску информации (OSINT / recon). Собрано параллельным прогоном агентов по категориям, звёзды и статус — по GitHub API на **2026-11-07**. Перед использованием любого инструмента смотри дату последнего коммита: в OSINT тулзы быстро ломаются и забрасываются.

**Легенда статуса:** Active = коммит за последние ~6 мес · Slow/Semi = 6–18 мес · Stale = >1–1.5 года · Archived = репозиторий архивирован/read-only.

> [!WARNING]
> **Граница каталога**
> Здесь только **легитимный FOSS** для авторизованной разведки, CTF и ресёрча. Сознательно **НЕ** каталогизированы как рабочие:
> - **«Пробив» по утечкам** — сервисы/боты, достающие ПДн чужих людей из слитых баз (combo-list, stealer-logs). Единственный допустимый breach-инструмент — **HaveIBeenPwned** (проверка *своей* засветки).
> - **Деанон по лицу** — PimEyes/FaceCheck/lenso-клоны и т.п. (поиск конкретного человека по фото).
> - Тулзы с заявкой «отследить геолокацию живого номера / резолв номер→личность→адрес» — это, как правило, маркетинг-оверклейм поверх библиотеки `phonenumbers`.
> Эти классы существуют и встречаются внутри некоторых awesome-листов ниже — при использовании списков триажить перед тем, как что-то брать.

---

## 0. С чего строить OSINT-проект (быстрый выбор)

- **Движок/агрегатор:** SpiderFoot (батарейки), либо Recon-ng (скриптуемый, воспроизводимый), либо BBOT (современный, рекурсивный) · графовый анализ связей — Flowsint / OpenCTI.
- **Username:** Maigret (досье) + Sherlock (быстрый обход) + WhatsMyName (данные-источник).
- **Email:** holehe (где зареган) + theHarvester (сбор по домену) + check-if-email-exists (валидация).
- **Домены/инфра:** Amass + subfinder + httpx + dnsx (ProjectDiscovery-стек).
- **Телефоны:** PhoneInfoga (формат/оператор/дорки).
- **Метаданные:** ExifTool.

Это полноценный легитимный инструмент авторизованной разведки с нормальной архитектурой под тесты и ревью.

---

## 1. Фреймворки, агрегаторы и каталоги

| Tool | Repo | Stars | Lang | Status | Назначение |
|---|---|---|---|---|---|
| SpiderFoot | smicallef/spiderfoot | ~24.4k | Python | Slowing (2026-04) | Автоматизация OSINT, 200+ модулей, web-UI + CLI. Footprint домена/IP/email/username. Часть модулей трогает ПДн — скоупить. |
| Recon-ng | lanmaster53/recon-ng | ~6.0k | Python | Active (2026-10) | Модульный recon-фреймворк в стиле Metasploit, workspace-БД. Скриптуемые пайплайны. |
| BBOT | blacklanternsecurity/bbot | ~11.0k | Python | Active (2026-11) | Рекурсивный модульный recon/attack-surface сканер. Часто зовут преемником SpiderFoot. |
| sn0int | kpcyrd/sn0int | ~2.6k | Rust | Active (2026-09) | Полуавтоматический OSINT-фреймворк со скриптовым движком, пакетным менеджером и локальной БД. |
| Flowsint | reconurge/flowsint | ~10.1k | TypeScript | Active (2026-10) | Новая графовая платформа OSINT-расследований; ближайший FOSS-аналог Maltego-link-analysis. |
| OGI (OpenGraph Intel) | khashashin/ogi | ~342 | Python | Active (2026-10) | Графовый link-analysis с моделью entity/transform, позиционируется как Maltego-альтернатива. |
| Seekr | seekr-osint/seekr | ~890 | Go | Slowing (2026-06) | Self-hosted all-in-one тулкит + дашборд, строит профили сущностей. |
| Web-Check | lissy93/web-check | ~35.4k | TypeScript | Active (2026-11) | Self-host дашборд website-OSINT: DNS, headers, TLS, стек, порты. |
| Mr.Holmes | Lucksi/Mr.Holmes | ~4.4k | Python | Semi (2026-02) | Агрегатор username/domain/phone-лукапов с отчётами. |
| Photon | s0md3v/Photon | ~13.3k | Python | Active (2026-10) | Быстрый краулер: вытаскивает URL, email, ключи, JS-endpoints, соц-ссылки. |
| reconftw | six2dez/reconftw | ~8.3k | Shell | Active (2026-11) | Готовый end-to-end recon-пайплайн (цепляет subfinder/httpx/nuclei и др.). |
| sn0int / X-osint / Nox | — | — | — | — | Прочие CLI-бандлеры; X-osint включает people-search — только в авторизованном скоупе. |

**Threat-intel / case-management / enrichment** (не чистый OSINT, но рядом): OpenCTI (`OpenCTI-Platform/opencti`, ~10.3k, Active) · IntelOwl (`intelowlproject/IntelOwl`, ~4.8k, Active, обогащение observables) · TheHive (`TheHive-Project/TheHive`, Scala, Archived 2025-07, 5.x ушёл в коммерцию) · Watcher (`thalesgroup-cert/Watcher`, ~1.4k, Active, мониторинг утечек/сквоттинга/CVE) · Mihari (`ninoseki/mihari`, ~946, Active, IOC-хантинг).

**Maltego** — проприетарный, не на GitHub; на GitHub живут community-трансформы (напр. `vognik/maltego-telegram`).

**Дистрибутивы/VM:** Trace Labs OSINT VM (`tracelabs/tlosint-live`, Stale) · RedHunt OS (`redhuntlabs/RedHunt-OS`, Stale).

### Каталоги / awesome-листы / методология

| Resource | Repo | Stars | Status | Назначение |
|---|---|---|---|---|
| awesome-osint | jivoi/awesome-osint | ~30.8k | Active | Канонический курированный список инструментов и источников. |
| OSINT Framework | lockfale/OSINT-Framework | ~12.4k | Active | Классическое дерево ресурсов по категориям (osintframework.com). |
| osint_stuff_tool_collection | cipher387/osint_stuff_tool_collection | ~9.1k | Active | Очень большая категоризированная коллекция с one-liner'ами. |
| Awesome-OSINT-List | Astrosp/Awesome-OSINT-List | ~4.6k | Active | Курированный список со скриптовой поддержкой. |
| awesome-osint-arsenal | rawfilejson/awesome-osint-arsenal | ~3.8k | Active | Большой арсенал; **триажить** на breach/lookup-сервисы перед переиспользованием. |
| OSINT-Cheat-sheet | Jieyab89/OSINT-Cheat-sheet | ~2.3k | Active | Чит-шит индекс тулз и техник. |
| awesome-osint-mcp-servers | soxoj/awesome-osint-mcp-servers | ~538 | Active | MCP-серверы для OSINT — чтобы LLM-агенты рулили recon-тулзами (2025-26). |
| Awesome-AI-OSINT | ubikron/Awesome-AI-OSINT | ~798 | Active | AI-assisted OSINT тулзы (2025-26). |
| awesome_osint_blockchain_analysis | aaarghhh/awesome_osint_blockchain_analysis | ~375 | Active | Крипто/блокчейн-расследования. |
| tracelabs/awesome-osint | tracelabs/awesome-osint | ~438 | Active | Список под missing-persons CTF. |
| OhShINT | OhShINT/ohshint.gitbook.io | ~980 | Stale (2024-08) | Методичка/handbook. |

---

## 2. Username / поиск аккаунтов по нику

| Tool | Repo | Stars | Lang | Status | Назначение |
|---|---|---|---|---|---|
| Sherlock | sherlock-project/sherlock | ~100k | Python | Active (2026-11) | Эталон: ник по 400+ сайтам, отдаёт найденные URL профилей. |
| Maigret | soxoj/maigret | ~39.8k | Python | Active (2026-11) | Досье по нику с ~3000 сайтов; парсит страницы профилей, рекурсит по найденным никам/ссылкам, Tor/I2P, отчёты HTML/PDF/JSON. |
| Social Analyzer | qeeqbox/social-analyzer | ~24.5k | JS | Semi (2026-01) | CLI/API/web, 1000+ сайтов, рейтинг совпадений + strings-detection. |
| Blackbird | antoniaci/blackbird | ~9.9k | Python | Active (2026-11) | Поиск по username и email на 600+ сайтах на данных WhatsMyName, AI-профайлинг, экспорт PDF/CSV. (старый путь p1ngul1n0/blackbird → 404) |
| Snoop | snooppr/snoop | ~4.1k | Python | Active (2026-10) | Сильная база СНГ/рус-сайтов + глобальные; web-БД и плагины. |
| GoSearch | ibnaleem/gosearch | ~3.9k | Go | Active (2026-11) | Быстрый поиск по 300+ сайтам. Есть breach-проверка — она вне скоупа, брать только username-часть. |
| WhatsMyName (WMN) | WebBreacher/WhatsMyName | ~3.0k | Python | Active (2026-11) | Community-JSON 700+ сайтов с правилами проверки. Источник данных для многих тулз. |
| socid-extractor | soxoj/socid-extractor | ~1.1k | Python | Active (2026-11) | Движок извлечения из страниц профиля (ID, связанные аккаунты), 150+ сайтов. Используется Maigret. |
| Marple | soxoj/marple | ~0.3k | Python | Active (2026-11) | Собирает ссылки на профили через поисковики (без пер-сайт проверок). Дополняет Maigret. |
| linkook | JackJuly/linkook | ~1.0k | Python | Active (2026-10) | Находит связанные аккаунты и email по username — анализ связей между профилями. |
| nexfil | thewhiteh4t/nexfil | ~2.6k | Python | Stale (2023-09) | Конкурентный поиск, Tor, свой список 350+ сайтов. |
| enola | TheYahya/enola | ~0.9k | Go | Semi (2026-07) | Go-CLI, «сестра Sherlock», 400+ сайтов. |
| Emora | idefasoft/Emora-Project | ~0.7k | C# | Semi (2026-02) | Sherlock-style с desktop-GUI. |
| OpenOSINT | OpenOSINT/OpenOSINT | ~1.9k | Python | Active (2026-11) | Тулкит для AI-агентов (Agent Skill, MCP, CLI); username — одна из возможностей. |

---

## 3. Email OSINT

**A. Registration-check (где email используется)**

| Tool | Repo | Stars | Lang | Status | Назначение |
|---|---|---|---|---|---|
| holehe | megadose/holehe | ~15.6k | Python | Slow (2024-09) | ~120 сайтов через reset/registration endpoints, без алерта владельцу. Классический первый шаг. |
| user-scanner | kaifcodec/user-scanner | ~5.6k | Python | Active (2026-11) | Email+username в одном, нативный MCP для LLM-агентов. |
| MailAccess | KatrielMoses/MailAccess | ~1.8k | Python | Active (2026-10) | Email-OSINT по 5000+ платформам с кластеризацией identity. Breach-часть — осторожно (вне скоупа). |
| socialscan | iojw/socialscan | ~1.9k | Python | Active (2026-10) | Lib+CLI: занят ли email/username на платформах. |
| mailcat | sharsil/mailcat | ~960 | Python | Active (2026-09) | Угадывает ящики по нику через SMTP/API провайдеров. |
| Zehef | N0rz3/Zehef | ~1.1k | Python | Slow (2024-11) | Трекер email: аккаунты, утечки, соц-профили. |

**B. Enrichment**

| Tool | Repo | Stars | Lang | Status | Назначение |
|---|---|---|---|---|---|
| GHunt | mxrch/GHunt | ~19.8k | Python | Active (2026-04) | Публичные данные Google-аккаунта по email (имя, Maps/Photos-активность, Calendar). Нужны cookies. |
| Mosint | alpkeskin/mosint | ~6.1k | Go | Slow (2024-02) | Автоматизированный email-OSINT: holehe-проверки + related emails + API. |
| iKy | kennbroorg/iKy | ~990 | Python | Active (2026-10) | Web-UI, собирает инфу по email и строит timeline. |
| email2phonenumber | martinvigo/email2phonenumber | ~2.8k | Python | Slow (2024-07) | Восстанавливает подсказки номера из reset-страниц. Для авторизованного теста. |

**C. Сбор email по домену**

| Tool | Repo | Stars | Lang | Status | Назначение |
|---|---|---|---|---|---|
| theHarvester | laramies/theHarvester | ~18.3k | Python | Active (2026-11) | Email/сабдомены/хосты/имена из поисковиков, CT-логов, API. Стандарт domain-recon. |
| EmailHarvester | maldevel/EmailHarvester | ~990 | Python | Active (2026-06) | Email для домена из поисковиков. |
| CrossLinked | m8sec/CrossLinked | ~1.6k | Python | Slow (2024-11) | Email-списки из имён LinkedIn через scraping поисковиков. |
| linkedin2username | initstring/linkedin2username | ~1.9k | Python | Active (2026-05) | Форматы username/email из штата компании в LinkedIn. |
| FinalRecon | thewhiteh4t/FinalRecon | ~3.0k | Python | Active (2026-10) | All-in-one web-recon с частичным сбором email. |

**D. Валидация (существует ли ящик)**

| Tool | Repo | Stars | Lang | Status | Назначение |
|---|---|---|---|---|---|
| check-if-email-exists | reacherhq/check-if-email-exists | ~10.4k | Rust | Active (2026-10) | SMTP-валидация без отправки письма, CLI+HTTP. Лицензия AGPL (есть коммерческая). |
| email-verifier | AfterShip/email-verifier | ~1.7k | Go | Active (2026-11) | Go-lib: syntax, MX, SMTP, disposable/role, Gravatar. |
| o365spray / o365enum / MailSniper | 0xZDH, gremwell, dafthack | — | — | — | O365/Exchange user-enum (+ спрей у o365spray/MailSniper). **Только авторизованный пентест.** |

**E. Breach — граница:** только **HaveIBeenPwned** (своя засветка, офиц. API). Сознательно НЕ в каталоге: h8mail, pwnedOrNot, cb-emailhunter и breach-модули — это lookup по слитым дампам/комбо-листам.

---

## 4. Домены / IP / инфраструктура / attack surface

Самая «белая» категория — пассивная разведка поверхности. Активные сканеры (masscan, ZMap, naabu, nuclei, ffuf, gobuster) шлют трафик в цель — **только с авторизацией.**

**Subdomain / asset discovery:** OWASP Amass (`owasp-amass/amass`, ~15.5k, Go, Active) · subfinder (`projectdiscovery/subfinder`, ~14.7k, Go, Active) · theHarvester (~18.3k) · Findomain (`Findomain/Findomain`, ~3.8k, Rust, Active) · Knockpy (`guelfoweb/knockpy`, ~4.2k) · BBOT (~11k) · uncover (`projectdiscovery/uncover`, запросы к Shodan/Censys/FOFA, нужны свои ключи) · cloudlist (активы из своих cloud-API) · Sublist3r (Stale), assetfinder (Stale).

**DNS:** dnsx (`projectdiscovery/dnsx`, Active) · dnsrecon (`darkoperator/dnsrecon`, ~3.1k, Active) · massdns (`blechschmidt/massdns`, ~3.7k, C) · shuffledns · puredns · Fierce.

**Порт/сервис/TLS:** Nmap (~13.9k) · masscan (~26.1k) · RustScan (`bee-san/RustScan`, ~20.7k) · naabu · ZMap/ZGrab2 · tlsx (имена из сертификатов) · asnmap · mapcidr · cdncheck.

**Web probing / crawling / content discovery:** httpx (`projectdiscovery/httpx`, ~10.6k, Active) · katana (`projectdiscovery/katana`, ~17.8k, краулер, headless) · Photon · hakrawler · gau (URL из Wayback/CommonCrawl/OTX) · waybackurls (Stale) · ParamSpider · ffuf (~17k) · gobuster (~14.3k) · gowitness (скриншоты) · EyeWitness · WhatWeb (fingerprint) · wafw00f (WAF-detect) · can-i-take-over-xyz (отпечатки subdomain-takeover) · Aquatone (Archived — заменён gowitness).

**Движки-пайплайны:** reconftw · recon-ng · OWASP Nettacker · nuclei (template-сканер, авторизованные цели) · interactsh (OOB) · notify (вывод в Slack/Discord/Telegram).

**Search-engine клиенты (нужны ключи):** censys-python (`censys/censys-python`) · Shodan Python lib/CLI (`achillean/shodan-python` — путь из памяти, сверить).

---

## 5. Телефонные номера

| Tool | Repo | Stars | Lang | Status | Назначение |
|---|---|---|---|---|---|
| PhoneInfoga | sundowndev/phoneinfoga | ~18.4k | Go | Active (2026-08) | Валидация/парсинг (страна, тип линии, оператор), генерация дорков, REST API + web-UI. Первый проход по номеру. |
| ignorant | megadose/ignorant | ~2.2k | Python | Stale (2024-07) | Зарегистрирован ли номер на Snapchat/Instagram/Amazon (по signup/reset-ответам). Сиблинг holehe. |
| telegram-phone-number-checker | bellingcat/telegram-phone-number-checker | ~1.9k | Python | Active (2026-08) | Есть ли у номеров Telegram-аккаунт (через Telegram API со своими кредами). |
| Phunter | N0rz3/Phunter | ~1.2k | Python | Stale (2024-04) | Валидность/оператор/тип линии/регион через `phonenumbers` + lookup API. |
| SearchPhone | HackUnderway/SearchPhone | ~2.1k | Python | Active (2026-08) | Агрегатор (формат/оператор/регион). «Tracking» в README — маркетинг; usable только carrier/region. |

> Репозитории с заголовком «track location by phone / phone→личность» — в основном обёртки над `phonenumbers` с оверклеймом. По открытым данным геолокацию живого номера они не дают; в каталог как рабочие не берём.

---

## 6. Соцсети (SOCMINT)

Самый короткий срок жизни — доверяй дате коммита и issues, не звёздам.

**Мульти-платформа / Google:** Sherlock, Maigret, Blackbird, WhatsMyName, socid-extractor (см. §2) · GHunt (`mxrch/GHunt`, ~19.8k, Google-аккаунт) · Bellingcat toolkit (`bellingcat/toolkit`) · gallery-dl (`mikf/gallery-dl`, ~20k, bulk-download медиа+метаданные) · ArchiveBox (`ArchiveBox/ArchiveBox`, ~29k, архивация страниц как доказательство).

**Instagram:** Instaloader (`instaloader/instaloader`, ~13.8k, Active — публичные профили/посты/stories/метаданные) · Osintgram (`Datalux/Osintgram`, ~15.5k, Active — интерактивный разбор аккаунта, нужен логин, часто ломается) · instagrapi (`subzeroid/instagrapi`, private-API клиент, ToS-риск) · Toutatis (`megadose/toutatis`, Stale) · instagram-location-search (`bellingcat/...`, гео по координатам).

**Twitter/X:** twscrape (`vladkens/twscrape`, ~2.9k, Active — сейчас один из живых) · twikit (`d60/twikit`, Active, API-free) · Scweet (Active) · tweepy (офиц. API) · snscrape (Dormant, Twitter-модуль сломан) · twint (Archived, историческое).

**Telegram:** Telepathy (`jordanwildon/Telepathy`, ~1.3k, Active — архив каналов/групп, member-листы, forward-сети) · tosint (`drego85/tosint`, разбор bot-token) · tg-archive (`knadh/tg-archive`, архив в статик-сайт) · Telethon/Pyrogram (MTProto-библиотеки, Archived — смотреть форки).

**TikTok/Reddit:** TikTok-Api (`davidteather/TikTok-Api`, ~6.7k, Active, нужен Playwright) · PRAW (`praw-dev/praw`, офиц. Reddit API) · tiktok-scraper (Dormant).

> Registration-checkers (ignorant, holehe) показывают только факт существования аккаунта; сайты их регулярно патчат.

---

## 7. Картинки / метаданные / документы

| Tool | Repo | Stars | Lang | Status | Назначение |
|---|---|---|---|---|---|
| ExifTool | exiftool/exiftool | ~5.2k | Perl | Active (2026-11) | Эталон чтения/записи метаданных (EXIF/XMP/IPTC/GPS) в фото/видео/PDF/Office. |
| exif-py | ianare/exif-py | ~975 | Python | Active (2026-06) | Чистый Python EXIF-ридер для пайплайнов. |
| oletools | decalage2/oletools | ~3.4k | Python | Active (2026-02) | Разбор OLE/Office: макросы, метаданные, embedded (DFIR/malware-триаж). |
| Apache Tika | apache/tika | ~4.1k | Java | Active (2026-11) | Тип + текст + метаданные из 1000+ форматов. |
| Tesseract | tesseract-ocr/tesseract | ~77k | C++ | Active (2026-11) | OCR для сканов/скриншотов в OSINT-пайплайне. |
| gallery-dl | mikf/gallery-dl | ~20k | Python | Active (2026-10) | Bulk-скачивание галерей со многих сайтов. |
| auto-archiver | bellingcat/auto-archiver | ~1.1k | Python | Active (2026-11) | Архивация контента с хешами/таймстемпами (доказательная база). |
| metagoofil | laramies/metagoofil | ~1.4k | Python | Slow (2024-03) | Находит публичные документы цели и тянет метаданные (авторы, софт, пути). |
| FOCA | ElevenPaths/FOCA | ~3.7k | C# | Stale (2022-12) | Windows: файлы на домене + метаданные/сетевые утечки. |

> **Деанон по лицу исключён** (PimEyes/FaceCheck/EagleEye-клоны — поиск человека по фото). Reverse-image-search обёртки (Google/Yandex/Bing, PicImageSearch) — не сверялись, использовать аккуратно.

---

## 8. Гео / GEOINT

| Tool | Repo | Stars | Lang | Status | Назначение |
|---|---|---|---|---|---|
| QGIS | qgis/QGIS | ~14.8k | C++ | Active | Десктоп-GIS с экосистемой плагинов. |
| GDAL | OSGeo/gdal | ~6.1k | C++ | Active | Перевод/обработка растровых и векторных геоданных. |
| OSMnx | gboeing/osmnx | ~5.9k | Python | Active | Загрузка/анализ уличных сетей и объектов OSM. |
| GeoPandas | geopandas/geopandas | ~5.3k | Python | Active | Геопространственные датафреймы. |
| geopy | geopy/geopy | ~4.9k | Python | Active | Геокодинг/обратный геокодинг по многим провайдерам. |
| leafmap | opengeos/leafmap | ~3.8k | Python | Active | Интерактивные карты/геоанализ в ноутбуках. |
| segment-geospatial | opengeos/segment-geospatial | ~4.2k | Python | Active | Сегментация объектов на спутнике (SAM). |
| overpass-turbo | tyrasd/overpass-turbo | ~1.3k | TS | Active | Web-UI запросов Overpass к OSM (объекты рядом с точкой). |
| mapillary_tools | mapillary/mapillary_tools | ~320 | Python | Active | Обработка/загрузка geotagged street-level снимков. |
| ukraine-timemap | bellingcat/ukraine-timemap | ~297 | JS | Active | Геопривязанный timemap инцидентов (эталон подхода). |

---

## 9. Компании / корпоративное / санкции

| Tool | Repo | Stars | Lang | Status | Назначение |
|---|---|---|---|---|---|
| OpenSanctions | opensanctions/opensanctions | ~867 | Python | Active | Краулеры/пайплайн по санкциям, PEP, компаниям. |
| yente | opensanctions/yente | ~185 | Python | Active | Entity-matching + поиск по данным OpenSanctions. |
| Aleph | alephdata/aleph | ~2.5k | JS | Maintenance (2026-02) | Платформа расследований по документам/публичным записям (OCCRP). |
| TruffleHog | trufflesecurity/trufflehog | ~29k | Go | Active | Поиск утёкших секретов в репах/файлах (leak-recon). |
| theHarvester / SpiderFoot / Photon | — | — | — | — | Для company-footprint (email/сабдомены/имена сотрудников). |

> OpenCorporates — офиц. API, проверенного FOSS-клиента не нашли.

---

## 10. Блокчейн

| Tool | Repo | Stars | Lang | Status | Назначение |
|---|---|---|---|---|---|
| GraphSense lib | graphsense/graphsense-lib | ~21 | Python | Active | Клиент к GraphSense (кластеризация/трассировка адресов). |
| mempool | mempool/mempool | ~2.9k | TS | Active | Open-source BTC-эксплорер/визуализатор мемпула для трассировки транзакций. |
| ethereum-etl | blockchain-etl/ethereum-etl | ~3.1k | Python | Slow (2026-01) | Экспорт блоков/транзакций/токен-трансферов ETH для анализа. |
| BlockSci | citp/BlockSci | ~1.4k | C++ | Unmaintained (2021) | Быстрый анализ/кластеризация BTC (research). |

---

## Не сверено

Из-за rate-limit GitHub API не подтверждены: Ominis-OSINT (путь репо), mailfy, часть Mastodon/Bluesky-тулз, reverse-image обёртки, slug Shodan-клиента. Перед использованием проверить руками. Статусы устаревают — смотри дату последнего коммита.
