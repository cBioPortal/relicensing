# RFC86 Phase 2 — Public Contributor Consent Status Board

**Status:** Updated 2026-07-10 — now includes contribution-time name/organization enrichment. Every contributor currently shows `pending` since Tier 1/Tier 2 outreach hasn't launched yet (scheduled Jul 13 / Jul 28 — see [relicensing#3](https://github.com/cBioPortal/relicensing/issues/3)). This board will be updated as responses come in.

This board lists every contributor to the 5 in-scope repos (`cbioportal`, `cbioportal-frontend`, `cbioportal-docker-compose`, `cbioportal-core`, `session-service`) by GitHub handle. **Name** and **Organization** use only public information, preferring contribution-time evidence over a possibly-blank or since-changed current GitHub profile:
- **Name**: current public GitHub profile name if set, otherwise the name recorded in their actual git commit history (also public — visible via `git log`/GitHub's commit API).
- **Organization**: the institution associated with their git commit author email **domain only** (e.g. `@mskcc.org` → MSKCC), preferring the oldest such signal found across each person's commit history (up to their 100 most recent commits) as a closer proxy for "organization at the time they were contributing," not their current employer. Falls back to the current GitHub profile "company" field if no institutional domain was found. **The raw email address itself is never shown or published** — only the resolved institution name, or nothing if no institution could be confidently identified (generic webmail and personal vanity domains are deliberately not mapped to an institution).

No email addresses, Slack IDs, or other private contact information appear anywhere in this file. That information is tracked separately and privately by the project team, per [relicensing#3](https://github.com/cBioPortal/relicensing/issues/3)'s "no raw contact info" requirement.

Precedent: [mpv's LGPL relicensing](https://github.com/mpv-player/mpv/issues/2033) used a similar public wiki page.

One bot account (`Copilot`, GitHub's AI coding agent) was excluded from this contributor list — AI authorship is tracked separately, see `docs/relicensing/dependency-audit.md`.

## Status legend

- `pending` — not yet contacted, or contacted and awaiting response
- `agreed` — has consented to relicensing their contributions to Apache-2.0
- `declined` — has explicitly declined
- `unreachable` — could not be located/contacted after reasonable effort (feeds the redirected "Vanish List" view)

## Contributors

| GitHub Handle | Last Commit | Name | Organization | Backend | Frontend | Docker Compose | Core (importer) | Session Service | Total | Consent Status |
|---|---|---|---|---|---|---|---|---|---|---|
| [inodb](https://github.com/inodb) | 2026-07-09 | Ino de Bruijn | @cBioPortal @genome-nexus @mskcc | 2130 | 1891 | 67 | 5 | 36 | 4129 | pending |
| [alisman](https://github.com/alisman) | 2026-07-08 | alisman |  | 413 | 3043 | 5 | 1 | 1 | 3463 | pending |
| [jjgao](https://github.com/jjgao) | 2024-11-24 | JJ Gao |  | 3169 | 11 | 0 | 0 | 0 | 3180 | pending |
| [n1zea144](https://github.com/n1zea144) | 2025-08-15 | n1zea144 |  | 2167 | 2 | 0 | 0 | 2 | 2171 | pending |
| [onursumer](https://github.com/onursumer) | 2026-06-17 | Onur Sumer | @mskcc | 1268 | 666 | 8 | 0 | 0 | 1942 | pending |
| [zhx828](https://github.com/zhx828) | 2023-07-25 | Hongxin | Oracle | 945 | 272 | 0 | 0 | 1 | 1218 | pending |
| [gideonite](https://github.com/gideonite) | 2015-04-22 | Gideon Dresdner | @brightbandtech | 818 | 2 | 0 | 0 | 0 | 820 | pending |
| [dippindots](https://github.com/dippindots) | 2026-07-10 | Gaofei Zhao |  | 402 | 246 | 39 | 20 | 8 | 715 | pending |
| [adamabeshouse](https://github.com/adamabeshouse) | 2022-04-13 | Adam Abeshouse |  | 62 | 630 | 1 | 0 | 0 | 693 | pending |
| [kalletlak](https://github.com/kalletlak) | 2024-09-30 | Karthik K |  | 256 | 396 | 0 | 0 | 11 | 663 | pending |
| [ecerami](https://github.com/ecerami) | 2026-04-10 | Ethan Cerami |  | 644 | 11 | 0 | 0 | 0 | 655 | pending |
| [fedde-s](https://github.com/fedde-s) | 2019-05-06 | Fedde Schaeffer | The Hyve | 487 | 50 | 0 | 0 | 0 | 537 | pending |
| [ersinciftci](https://github.com/ersinciftci) | 2019-04-19 | Ersin Ciftci |  | 366 | 82 | 0 | 0 | 0 | 448 | pending |
| [pvannierop](https://github.com/pvannierop) | 2024-05-07 | Pim van Nierop | The Hyve | 156 | 272 | 6 | 0 | 2 | 436 | pending |
| [armish](https://github.com/armish) | 2015-06-09 | B. Arman Aksoy |  | 315 | 0 | 0 | 0 | 0 | 315 | pending |
| [zainasir](https://github.com/zainasir) | 2026-07-09 | Zain Nasir |  | 106 | 66 | 83 | 1 | 2 | 258 | pending |
| [gblaih](https://github.com/gblaih) | 2026-07-09 | Bryan Lai | MSKCC | 16 | 183 | 0 | 1 | 4 | 204 | pending |
| [pieterlukasse](https://github.com/pieterlukasse) | 2025-04-17 | pieterlukasse |  | 190 | 10 | 0 | 0 | 0 | 200 | pending |
| [sheridancbio](https://github.com/sheridancbio) | 2026-05-23 | Robert Sheridan | MSKCC | 171 | 5 | 1 | 14 | 0 | 191 | pending |
| [oplantalech](https://github.com/oplantalech) | 2026-03-31 | Oleguer Plantalech | The Hyve | 108 | 72 | 0 | 4 | 2 | 186 | pending |
| [leexgh](https://github.com/leexgh) | 2025-12-22 | Xiang Li | University of Missouri | 16 | 143 | 0 | 0 | 0 | 159 | pending |
| [mandawilson](https://github.com/mandawilson) | 2026-06-16 | Manda Wilson | MSKCC | 71 | 1 | 0 | 0 | 87 | 159 | pending |
| [zheins](https://github.com/zheins) | 2017-05-26 | Zachary Heins |  | 157 | 0 | 0 | 0 | 0 | 157 | pending |
| [haynescd](https://github.com/haynescd) | 2025-07-14 | Charles Haynes | CHOP | 78 | 39 | 5 | 19 | 0 | 141 | pending |
| [Luke-Sikina](https://github.com/Luke-Sikina) | 2023-01-19 | Luke Sikina | DFCI | 61 | 54 | 3 | 0 | 2 | 120 | pending |
| [yichaoS](https://github.com/yichaoS) | 2022-05-04 | Yichao Sun | MSKCC | 100 | 15 | 0 | 0 | 0 | 115 | pending |
| [istemi-bahceci](https://github.com/istemi-bahceci) | 2016-08-16 | İstemi Bahçeci |  | 109 | 0 | 0 | 0 | 0 | 109 | pending |
| [JiaoJiao123](https://github.com/JiaoJiao123) | 2017-07-28 | Jiaojiao Wang |  | 97 | 1 | 0 | 0 | 0 | 98 | pending |
| [ao508](https://github.com/ao508) | 2025-06-24 | ao508 |  | 90 | 5 | 0 | 0 | 1 | 96 | pending |
| [adufilie](https://github.com/adufilie) | 2016-12-16 | Andrew Dufilie |  | 0 | 80 | 0 | 0 | 0 | 80 | pending |
| [nschultz-sketch](https://github.com/nschultz-sketch) | 2012-08-06 | Nikolaus Schultz | MSKCC | 79 | 0 | 0 | 0 | 0 | 79 | pending |
| [tmazor](https://github.com/tmazor) | 2026-05-20 | Tali Mazor | DFCI | 70 | 4 | 0 | 0 | 0 | 74 | pending |
| [JREastonMarks](https://github.com/JREastonMarks) | 2025-02-28 | Jeremy R. Easton-Marks |  | 42 | 0 | 1 | 28 | 0 | 71 | pending |
| [spcar7](https://github.com/spcar7) | 2011-08-24 | lennartbastian |  | 69 | 0 | 0 | 0 | 0 | 69 | pending |
| [ritikakundra](https://github.com/ritikakundra) | 2025-01-08 | ritikakundra | MSKCC | 61 | 0 | 0 | 0 | 0 | 61 | pending |
| [nr23730](https://github.com/nr23730) | 2024-04-29 | Niklas Reimer | @skfit-uni-luebeck | 49 | 1 | 6 | 5 | 0 | 61 | pending |
| [caitlinjones](https://github.com/caitlinjones) | 2011-12-21 | Caitlin Byrne |  | 58 | 0 | 0 | 0 | 0 | 58 | pending |
| [rmadupuri](https://github.com/rmadupuri) | 2026-03-31 | Ramya Madupuri | Memorial Sloan Kettering Cancer Center | 49 | 0 | 3 | 6 | 0 | 58 | pending |
| [tamaccount](https://github.com/tamaccount) | 2017-10-16 | Tamba | MIT | 4 | 48 | 0 | 0 | 0 | 52 | pending |
| [sbabyanusha](https://github.com/sbabyanusha) | 2026-04-07 | sbabyanusha | MSKCC | 42 | 0 | 0 | 10 | 0 | 52 | pending |
| [jagnathan](https://github.com/jagnathan) | 2024-05-03 | Jag (P K Jagannathan) |  | 25 | 24 | 0 | 0 | 0 | 49 | pending |
| [morungos](https://github.com/morungos) | 2016-07-19 | Stuart Watt |  | 48 | 0 | 0 | 0 | 0 | 48 | pending |
| [forus](https://github.com/forus) | 2026-04-01 | Ruslan Forostianov | SE4BIO | 15 | 4 | 2 | 16 | 9 | 46 | pending |
| [averyniceday](https://github.com/averyniceday) | 2025-01-10 | Avery Wang | MSKCC | 39 | 2 | 0 | 0 | 0 | 41 | pending |
| [victoria34](https://github.com/victoria34) | 2020-04-09 | Jing Su | Memorial Sloan Kettering Cancer Center | 20 | 18 | 0 | 0 | 0 | 38 | pending |
| [fuzhaoyuan](https://github.com/fuzhaoyuan) | 2026-02-19 | Zhaoyuan (Ryan) Fu | Dana-Farber Cancer Institute | 18 | 16 | 2 | 0 | 0 | 36 | pending |
| [furkansahin](https://github.com/furkansahin) | 2015-09-21 | Furkan Sahin | Ubicloud | 33 | 0 | 0 | 0 | 0 | 33 | pending |
| [qlu-cls](https://github.com/qlu-cls) | 2024-05-02 | Qi-Xuan Lu | Caris Life Sciences | 30 | 2 | 0 | 0 | 0 | 32 | pending |
| [schultzn](https://github.com/schultzn) | 2022-04-30 | Nikolaus Schultz | MSKCC | 26 | 0 | 0 | 0 | 0 | 26 | pending |
| [j-hudecek](https://github.com/j-hudecek) | 2019-12-17 | j-hudecek | Netherlands Cancer Institute (NKI) | 24 | 0 | 0 | 0 | 0 | 24 | pending |
| [TJMKuijpers](https://github.com/TJMKuijpers) | 2025-10-14 | Tim Kuijpers | The Hyve | 2 | 20 | 0 | 1 | 0 | 23 | pending |
| [brittanydionigi](https://github.com/brittanydionigi) | 2017-03-24 | Brittany Dionigi | google | 22 | 0 | 0 | 0 | 0 | 22 | pending |
| [amirinenik](https://github.com/amirinenik) | 2020-04-08 | Kiran Amirineni | NIH | 2 | 19 | 0 | 0 | 0 | 21 | pending |
| [leedonghn4](https://github.com/leedonghn4) | 2015-06-29 | Dong Li |  | 20 | 0 | 0 | 0 | 0 | 20 | pending |
| [ngocnn1104](https://github.com/ngocnn1104) | 2020-02-10 | Ngoc Nguyen | @welldium | 2 | 16 | 0 | 0 | 0 | 18 | pending |
| [jamesqo](https://github.com/jamesqo) | 2026-06-10 | James Ko | Memorial Sloan Kettering | 10 | 0 | 1 | 7 | 0 | 18 | pending |
| [Rajat-Sirohi](https://github.com/Rajat-Sirohi) | 2021-08-18 | Rajat Sirohi |  | 4 | 13 | 0 | 0 | 0 | 17 | pending |
| [jtquach1](https://github.com/jtquach1) | 2021-01-05 | Joyce Quach |  | 4 | 12 | 0 | 0 | 0 | 16 | pending |
| [HectorWon](https://github.com/HectorWon) | 2015-05-28 | Minxin Cheng |  | 14 | 0 | 0 | 0 | 0 | 14 | pending |
| [lemccarthy](https://github.com/lemccarthy) | 2019-05-08 | Lloyd McCarthy |  | 8 | 5 | 0 | 0 | 0 | 13 | pending |
| [uklineale](https://github.com/uklineale) | 2024-02-09 | Neel Kuila |  | 10 | 2 | 0 | 0 | 0 | 12 | pending |
| [ChrisWakefield](https://github.com/ChrisWakefield) | 2020-01-15 | Chris Wakefield | MD Anderson Cancer Center | 8 | 4 | 0 | 0 | 0 | 12 | pending |
| [pappde](https://github.com/pappde) | 2024-09-23 | Denis P | Arriboworks, LLC | 7 | 4 | 0 | 0 | 0 | 11 | pending |
| [paragomi](https://github.com/paragomi) | 2012-07-05 | nkucukdemirci |  | 10 | 0 | 0 | 0 | 0 | 10 | pending |
| [priti88](https://github.com/priti88) | 2016-01-24 | Priti Kumari | Dana Farber Cancer Institute | 10 | 0 | 0 | 0 | 0 | 10 | pending |
| [rnugraha](https://github.com/rnugraha) | 2018-04-16 | Riza Nugraha |  | 6 | 3 | 0 | 0 | 0 | 9 | pending |
| [MatthijsPon](https://github.com/MatthijsPon) | 2024-10-21 | Matthijs Pon | The Hyve | 4 | 2 | 0 | 3 | 0 | 9 | pending |
| [holtgrewe](https://github.com/holtgrewe) | 2020-04-17 | Manuel Holtgrewe | Charité – Universitätsmedizin Berlin | 8 | 0 | 0 | 0 | 0 | 8 | pending |
| [msalihaltun](https://github.com/msalihaltun) | 2021-05-26 | Salih Altun |  | 0 | 8 | 0 | 0 | 0 | 8 | pending |
| [dionnezaal](https://github.com/dionnezaal) | 2017-12-07 | dionnezaal |  | 8 | 0 | 0 | 0 | 0 | 8 | pending |
| [artgoldberg](https://github.com/artgoldberg) | 2011-12-08 | Arthur P Goldberg | Arthur Goldberg Consulting, LLC | 7 | 0 | 0 | 0 | 0 | 7 | pending |
| [Nelliney](https://github.com/Nelliney) | 2025-01-10 | Tetiana |  | 0 | 7 | 0 | 0 | 0 | 7 | pending |
| [dubincorey](https://github.com/dubincorey) | 2023-03-09 | Corey Dubin |  | 0 | 7 | 0 | 0 | 0 | 7 | pending |
| [rishisulakhe](https://github.com/rishisulakhe) | 2026-02-23 | Rishi Prasad Sulakhe |  | 1 | 6 | 0 | 0 | 0 | 7 | pending |
| [hweej](https://github.com/hweej) | 2024-12-30 | Jason Hwee |  | 4 | 3 | 0 | 0 | 0 | 7 | pending |
| [cataphract](https://github.com/cataphract) | 2015-07-30 | Gustavo Lopes | The Hyve | 6 | 0 | 0 | 0 | 0 | 6 | pending |
| [johnyesit](https://github.com/johnyesit) | 2025-06-09 | johnyesit | NIH | 0 | 6 | 0 | 0 | 0 | 6 | pending |
| [Beking0912](https://github.com/Beking0912) | 2023-08-24 | Beking0912 |  | 1 | 5 | 0 | 0 | 0 | 6 | pending |
| [juleskers](https://github.com/juleskers) | 2015-08-31 | Jules Kerssemakers | DKFZ (German Cancer Research Center) | 6 | 0 | 0 | 0 | 0 | 6 | pending |
| [arishta](https://github.com/arishta) | 2025-01-07 | Arishta Jain |  | 1 | 4 | 0 | 0 | 0 | 5 | pending |
| [Pradyuman-aviator](https://github.com/Pradyuman-aviator) | 2026-06-24 | DevPradyumansh. | NIT Hamirpur | 5 | 0 | 0 | 0 | 0 | 5 | pending |
| [agarwalrounak](https://github.com/agarwalrounak) | 2019-03-17 | Rounak Agarwal |  | 2 | 3 | 0 | 0 | 0 | 5 | pending |
| [sowmiyaa-kumar](https://github.com/sowmiyaa-kumar) | 2025-03-28 | Sowmiyaa Kumar |  | 4 | 1 | 0 | 0 | 0 | 5 | pending |
| [tlangs](https://github.com/tlangs) | 2016-04-21 | Trevyn Langsford | Layer Health | 5 | 0 | 0 | 0 | 0 | 5 | pending |
| [i-am-leslie](https://github.com/i-am-leslie) | 2026-06-29 | Leslie |  | 2 | 2 | 0 | 0 | 0 | 4 | pending |
| [kojix2](https://github.com/kojix2) | 2024-10-29 | kojix2 |  | 1 | 0 | 3 | 0 | 0 | 4 | pending |
| [jfkonecn](https://github.com/jfkonecn) | 2023-09-10 | John Konecny |  | 1 | 3 | 0 | 0 | 0 | 4 | pending |
| [aditygrg2](https://github.com/aditygrg2) | 2023-05-30 | Aditya Garg |  | 0 | 4 | 0 | 0 | 0 | 4 | pending |
| [coderrsid](https://github.com/coderrsid) | 2019-03-22 | Siddhant Sehgal |  | 0 | 4 | 0 | 0 | 0 | 4 | pending |
| [jxu8](https://github.com/jxu8) | 2018-08-31 | jxu8 | Columbia University | 0 | 4 | 0 | 0 | 0 | 4 | pending |
| [alexsigaras](https://github.com/alexsigaras) | 2017-09-18 | Alexandros Sigaras | Weill Cornell Medicine | 4 | 0 | 0 | 0 | 0 | 4 | pending |
| [egarcialara](https://github.com/egarcialara) | 2022-11-28 | Elena |  | 4 | 0 | 0 | 0 | 0 | 4 | pending |
| [YusufZiyaOzgul](https://github.com/YusufZiyaOzgul) | 2023-01-13 | YusufZiyaOzgul |  | 0 | 3 | 0 | 0 | 0 | 3 | pending |
| [bemijonathan](https://github.com/bemijonathan) | 2024-09-19 | Jonathan Atiene | @Hive-Science | 0 | 3 | 0 | 0 | 0 | 3 | pending |
| [aderidder](https://github.com/aderidder) | 2016-03-07 | Sander de Ridder |  | 3 | 0 | 0 | 0 | 0 | 3 | pending |
| [Spenca](https://github.com/Spenca) | 2020-04-22 | Spencer Vatrt-Watts | @QryptInc | 3 | 0 | 0 | 0 | 0 | 3 | pending |
| [olzhasmukayev](https://github.com/olzhasmukayev) | 2024-04-01 | Olzhas Mukayev |  | 0 | 3 | 0 | 0 | 0 | 3 | pending |
| [Leowisd](https://github.com/Leowisd) | 2021-01-12 | Yifu |  | 0 | 3 | 0 | 0 | 0 | 3 | pending |
| [ugurdogrusoz](https://github.com/ugurdogrusoz) | 2012-05-07 | ugurdogrusoz |  | 3 | 0 | 0 | 0 | 0 | 3 | pending |
| [FlorisVleugels](https://github.com/FlorisVleugels) | 2025-07-30 | Melrus |  | 1 | 2 | 0 | 0 | 0 | 3 | pending |
| [khaledfahmy123](https://github.com/khaledfahmy123) | 2024-04-15 | Khaled Fahmy | None | 0 | 3 | 0 | 0 | 0 | 3 | pending |
| [sambrightman](https://github.com/sambrightman) | 2016-09-15 | Sam Brightman |  | 3 | 0 | 0 | 0 | 0 | 3 | pending |
| [fkaercher](https://github.com/fkaercher) | 2015-07-16 | Florian Kaercher | DKFZ (German Cancer Research Center) | 3 | 0 | 0 | 0 | 0 | 3 | pending |
| [Djokovic0311](https://github.com/Djokovic0311) | 2023-08-22 | Jiahang Li |  | 2 | 1 | 0 | 0 | 0 | 3 | pending |
| [kunalhemnani1](https://github.com/kunalhemnani1) | 2026-02-24 | Kunal Hemnani |  | 0 | 2 | 0 | 0 | 0 | 2 | pending |
| [ayushns9](https://github.com/ayushns9) | 2019-03-18 | Ayush Goel | Stripe | 0 | 2 | 0 | 0 | 0 | 2 | pending |
| [saurabhhhcodes](https://github.com/saurabhhhcodes) | 2026-03-20 | Saurabh Kumar Bajpai | Akoode Technologies | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [marriott-er](https://github.com/marriott-er) | 2018-09-26 | Eric Marriott | DFCI | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [pozhidaevak](https://github.com/pozhidaevak) | 2025-01-31 | Anton Pozhidaev |  | 1 | 1 | 0 | 0 | 0 | 2 | pending |
| [brettvanderwerff](https://github.com/brettvanderwerff) | 2019-04-04 | Brett Vanderwerff |  | 0 | 2 | 0 | 0 | 0 | 2 | pending |
| [SURAJ-SHARMA27](https://github.com/SURAJ-SHARMA27) | 2025-01-27 | SURAJ |  | 0 | 2 | 0 | 0 | 0 | 2 | pending |
| [KingAlex1985](https://github.com/KingAlex1985) | 2025-05-02 | KingAlex1985 |  | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [SAHU-01](https://github.com/SAHU-01) | 2024-03-29 | Ankita Sahu | ZkAGI | 0 | 2 | 0 | 0 | 0 | 2 | pending |
| [ckandoth](https://github.com/ckandoth) | 2015-11-18 | Cyriac Kandoth | Penn Medicine | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [dianab0](https://github.com/dianab0) | 2022-02-22 | dianab0 |  | 1 | 1 | 0 | 0 | 0 | 2 | pending |
| [lllinging](https://github.com/lllinging) | 2025-05-06 | lllinging |  | 0 | 2 | 0 | 0 | 0 | 2 | pending |
| [amanbhardwaj12072003](https://github.com/amanbhardwaj12072003) | 2024-03-01 | Aman Bhardwaj |  | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [ugurkoysuren](https://github.com/ugurkoysuren) | 2024-08-27 | Ugur Koysuren |  | 1 | 0 | 1 | 0 | 0 | 2 | pending |
| [sayan-aiml](https://github.com/sayan-aiml) | 2026-05-18 | Sayan Kr. Pattanayak |  | 0 | 2 | 0 | 0 | 0 | 2 | pending |
| [kurt-mueller-osumc](https://github.com/kurt-mueller-osumc) | 2020-09-16 | Kurt Mueller | The Ohio State University College of Medicine Research IT | 1 | 0 | 1 | 0 | 0 | 2 | pending |
| [dtenenba](https://github.com/dtenenba) | 2020-12-09 | Dan Tenenbaum | Fred Hutchinson Cancer Center | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [VenkateshVishwas](https://github.com/VenkateshVishwas) | 2025-02-04 | Venky |  | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [johnyaku](https://github.com/johnyaku) | 2021-03-15 | John Reeves | Garvan Institute of Medical Research | 1 | 0 | 1 | 0 | 0 | 2 | pending |
| [VarshiniGunti](https://github.com/VarshiniGunti) | 2026-04-07 | Varshini | Indian institute of technology Bhilai | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [siddhiguptas](https://github.com/siddhiguptas) | 2026-03-31 | Siddhi Gupta |  | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [tweep](https://github.com/tweep) | 2020-05-15 | Jan-Hinnerk Vogel | Open to new opportunities | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [vaibhavlachhwani](https://github.com/vaibhavlachhwani) | 2024-11-30 | Vaibhav Lachhwani |  | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [gritsynad](https://github.com/gritsynad) | 2025-07-15 | Gritsyna Dmitriy |  | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [gautamsarawagi](https://github.com/gautamsarawagi) | 2024-08-19 | Gautam Sarawagi |  | 0 | 2 | 0 | 0 | 0 | 2 | pending |
| [tonatiuh-gonzalez47](https://github.com/tonatiuh-gonzalez47) | 2021-08-11 | Tonatiuh Gonzalez |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [scvannost](https://github.com/scvannost) | 2023-12-20 | SC Van Nostrand |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [eugeniomazzone](https://github.com/eugeniomazzone) | 2025-02-28 | Eugenio Mazzone | University of Turin | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [KhushamBansal](https://github.com/KhushamBansal) | 2025-12-29 | Khusham Bansal |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [aswin2108](https://github.com/aswin2108) | 2022-03-23 | Aswin Shailajan | Vellore Institute of Technology | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [m12m3r](https://github.com/m12m3r) | 2025-02-04 | Mark Shehata |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [Vignesh-JavaDev](https://github.com/Vignesh-JavaDev) | 2025-06-17 | Vignesh-JavaDev |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [viveak910](https://github.com/viveak910) | 2025-06-12 | viveak |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [scbaysal](https://github.com/scbaysal) | 2016-05-05 | eightbit |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [jorvis](https://github.com/jorvis) | 2025-11-11 | Joshua Orvis | Institute for Genome Sciences | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [er-abhijeet](https://github.com/er-abhijeet) | 2025-02-04 | Abhijeet M |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [PerVillalva](https://github.com/PerVillalva) | 2026-04-10 | Percival Villalva |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [mhsh312](https://github.com/mhsh312) | 2024-04-25 | mhsh312 |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [karissawhiting](https://github.com/karissawhiting) | 2023-06-09 | karissawhiting |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [Gautam-aman](https://github.com/Gautam-aman) | 2026-02-19 | Aman Gautam |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [gulshan2052](https://github.com/gulshan2052) | 2025-06-26 | Gulshan Anand |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [callachennault](https://github.com/callachennault) | 2026-05-07 | Calla Chennault |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [manik-dhanjal](https://github.com/manik-dhanjal) | 2023-02-25 | Manik Dhanjal | Escorts Kubota Limited | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [YashhCanCode](https://github.com/YashhCanCode) | 2026-02-24 | Yashwanth Konnuru | Marri Laxman Reddy of institute of technology and management | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [pambot](https://github.com/pambot) | 2017-08-09 | Pambot | Shopify | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [Injora](https://github.com/Injora) | 2026-01-26 | Injora |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [hskarlupka](https://github.com/hskarlupka) | 2021-04-07 | Heath Skarlupka | University of Wisconsin-Madison | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [sanki92](https://github.com/sanki92) | 2026-02-02 | Sankalp Tripathi |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [pcvolkmer](https://github.com/pcvolkmer) | 2022-10-24 | Paul-Christian Volkmer |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [gorkemsolun](https://github.com/gorkemsolun) | 2023-08-02 | Görkem Kadir Solun | ETH Zürich | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [Zohaibarif69](https://github.com/Zohaibarif69) | 2026-04-01 | ZOHAIB |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [Aiosa](https://github.com/Aiosa) | 2025-02-18 | Aiosa |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [officialasishkumar](https://github.com/officialasishkumar) | 2026-07-06 | Asish Kumar |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [rohangoel96](https://github.com/rohangoel96) | 2016-07-19 | Rohan Goel |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [zeynepkaragoz](https://github.com/zeynepkaragoz) | 2024-10-08 | Zeynep Karagoz, PhD | @thehyve | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [RyukXO-code](https://github.com/RyukXO-code) | 2026-02-11 | Sagnik |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [teesamuel](https://github.com/teesamuel) | 2025-02-22 | Samuel Olufemi | Silverrail Technology | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [agandolf](https://github.com/agandolf) | 2020-04-17 | agandolf | University of Michigan | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [justinjao](https://github.com/justinjao) | 2023-05-19 | Justin Jao |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [anthony-cros](https://github.com/anthony-cros) | 2016-08-04 | Anthony Cros | Software architect | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [rishav-raj-genx](https://github.com/rishav-raj-genx) | 2026-02-24 | Rishav Raj |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [gauravbyte](https://github.com/gauravbyte) | 2025-03-18 | Gaurav Chaudhari | IIT Madras CSE | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [Annu881](https://github.com/Annu881) | 2026-02-09 | Annu881 |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [thomasmarwitz](https://github.com/thomasmarwitz) | 2025-05-13 | thomasmarwitz |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [mdhvprasad](https://github.com/mdhvprasad) | 2020-04-17 | mvprasad |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [NikdAK](https://github.com/NikdAK) | 2020-12-17 | Niklas dAK | Technical University of Munich | 0 | 0 | 1 | 0 | 0 | 1 | pending |
| [anshuman-rai-27](https://github.com/anshuman-rai-27) | 2024-12-30 | Anshuman Rai | @soundversegit | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [nbentoneves](https://github.com/nbentoneves) | 2024-11-15 | Nuno Bento |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [meow1729](https://github.com/meow1729) | 2017-04-01 | Prophet_MEOW |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [jochemb](https://github.com/jochemb) | 2016-07-01 | Jochem Bijlard |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [yashhash2](https://github.com/yashhash2) | 2024-11-21 | Yash Kumar Singh |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [stevearmstrong-dev](https://github.com/stevearmstrong-dev) | 2026-03-25 | Steve Armstrong |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [Rgtemze](https://github.com/Rgtemze) | 2019-07-09 | Ziya ERKOC | Bilkent University | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [thepiyush-303](https://github.com/thepiyush-303) | 2025-01-17 | Piyush Bhatt |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [mervekilicarslan5](https://github.com/mervekilicarslan5) | 2020-07-16 | Merve Kılıçarslan | @TUM | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [pnartowski](https://github.com/pnartowski) | 2025-04-16 | Nartowski Paweł |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [kunalchandan](https://github.com/kunalchandan) | 2019-01-18 | Kunal Chandan | MicroAlchemy Inc. @microAlchemy | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [waffle-iron](https://github.com/waffle-iron) | 2015-11-17 | Making GitHub Delicious. | Rally Software | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [saxenanurag](https://github.com/saxenanurag) | 2026-03-31 | Anurag Saxena | Cleveland Clinic Research | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [FilledEther20](https://github.com/FilledEther20) | 2025-01-29 | Chaitanya Gairola |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [Player256](https://github.com/Player256) | 2023-04-29 | space_samurai |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [khzhu](https://github.com/khzhu) | 2017-04-15 | Kelsey Zhu |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [ShahKirtan2003](https://github.com/ShahKirtan2003) | 2025-01-27 | Kirtan Shah |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [Vinny02](https://github.com/Vinny02) | 2024-06-03 | Vinny02 |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [ruslan-forostianov](https://github.com/ruslan-forostianov) | 2022-04-12 | Ruslan Forostianov |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [eliaslautensack](https://github.com/eliaslautensack) | 2026-05-24 | eliaslautensack | University Medical Center Göttingen | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [Ak-Macha](https://github.com/Ak-Macha) | 2021-07-29 | Ak-Matcha |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [emmanuel-ferdman](https://github.com/emmanuel-ferdman) | 2025-01-02 | Emmanuel Ferdman |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [heuermh](https://github.com/heuermh) | 2016-04-14 | Michael L Heuer | Stealth-Mode Biotech | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [calvinlu3](https://github.com/calvinlu3) | 2021-09-10 | Calvin Lu |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [stachnim](https://github.com/stachnim) | 2016-04-14 | Marcin Stachniuk | Roche | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [GarvitDadheech](https://github.com/GarvitDadheech) | 2025-01-17 | Garvit Dadheech |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [Ismael-Sallami](https://github.com/Ismael-Sallami) | 2026-02-10 | Ismael Sallami |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [MizeroR](https://github.com/MizeroR) | 2026-03-25 | Reine Mizero |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [chandrikarj](https://github.com/chandrikarj) | 2025-01-03 | Chandrika |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [rosh2525](https://github.com/rosh2525) | 2026-03-02 | Roshan | IIT Jodhpur | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [HarshithaSivalingala](https://github.com/HarshithaSivalingala) | 2026-03-23 | Sai Harshitha Sivalingala |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [jCHENEBY](https://github.com/jCHENEBY) | 2025-01-16 | jCHENEBY | UIO Oslo, Elixir Norway | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [scarrero4660](https://github.com/scarrero4660) | 2023-01-10 | scarrero4660 |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [sandertan](https://github.com/sandertan) | 2016-09-02 | Sander Tan |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [chiang-sh](https://github.com/chiang-sh) | 2025-09-05 | Shan Chiang | Taipei Medical University | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [codyharoldsen](https://github.com/codyharoldsen) | 2019-08-09 | sharoldsen |  | 0 | 0 | 0 | 0 | 1 | 1 | pending |
| [jonkiky](https://github.com/jonkiky) | 2025-09-01 | Yizhen Chen |  | 0 | 0 | 0 | 0 | 1 | 1 | pending |
| [sdpetrides](https://github.com/sdpetrides) | 2021-09-10 | Stephen Petrides | @nadeemlab | 0 | 0 | 0 | 0 | 1 | 1 | pending |
| [sgicbpc](https://github.com/sgicbpc) | 2023-12-05 | sgicbpc |  | 0 | 0 | 0 | 1 | 0 | 1 | pending |
