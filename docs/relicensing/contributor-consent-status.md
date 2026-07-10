# RFC86 Phase 2 — Public Contributor Consent Status Board

**Status:** Updated 2026-07-10 — now covers all 5 in-scope repos (`cbioportal`, `cbioportal-frontend`, `cbioportal-docker-compose`, `cbioportal-core`, `session-service`). Every contributor currently shows `pending` since Tier 1/Tier 2 outreach hasn't launched yet (scheduled Jul 13 / Jul 28 — see [relicensing#3](https://github.com/cBioPortal/relicensing/issues/3)). This board will be updated as responses come in.

This board lists every contributor to the 5 repos above by GitHub handle, using only information they've chosen to make public on their GitHub profile (name and company fields, fetched directly from the public GitHub API on 2026-07-10) — no email addresses, Slack IDs, or other private contact information. That information is tracked separately and privately by the project team, per [relicensing#3](https://github.com/cBioPortal/relicensing/issues/3)'s "no raw contact info" requirement.

Precedent: [mpv's LGPL relicensing](https://github.com/mpv-player/mpv/issues/2033) used a similar public wiki page.

`cbioportal-docker-compose`, `cbioportal-core`, and `session-service` are lightweight/newer repos — most of their contributors already appear below via the main `cbioportal`/`cbioportal-frontend` repos. Only 4 people (`codyharoldsen`, `jonkiky`, `sdpetrides`, `sgicbpc`) were net-new. One bot account (`Copilot`, GitHub's AI coding agent) was excluded from this contributor list — AI authorship is tracked separately, see `docs/relicensing/dependency-audit.md`.

## Status legend

- `pending` — not yet contacted, or contacted and awaiting response
- `agreed` — has consented to relicensing their contributions to Apache-2.0
- `declined` — has explicitly declined
- `unreachable` — could not be located/contacted after reasonable effort (feeds the redirected "Vanish List" view)

## Contributors

| GitHub Handle | Public Name | Public Company/Institution | Backend | Frontend | Docker Compose | Core (importer) | Session Service | Total | Consent Status |
|---|---|---|---|---|---|---|---|---|---|
| [inodb](https://github.com/inodb) | Ino de Bruijn | @cBioPortal @genome-nexus @mskcc | 2130 | 1891 | 67 | 5 | 36 | 4129 | pending |
| [alisman](https://github.com/alisman) |  |  | 413 | 3043 | 5 | 1 | 1 | 3463 | pending |
| [jjgao](https://github.com/jjgao) |  |  | 3169 | 11 | 0 | 0 | 0 | 3180 | pending |
| [n1zea144](https://github.com/n1zea144) |  |  | 2167 | 2 | 0 | 0 | 2 | 2171 | pending |
| [onursumer](https://github.com/onursumer) | Onur Sumer | @mskcc | 1268 | 666 | 8 | 0 | 0 | 1942 | pending |
| [zhx828](https://github.com/zhx828) | Hongxin | Oracle | 945 | 272 | 0 | 0 | 1 | 1218 | pending |
| [gideonite](https://github.com/gideonite) | Gideon Dresdner | @brightbandtech | 818 | 2 | 0 | 0 | 0 | 820 | pending |
| [dippindots](https://github.com/dippindots) | Gaofei Zhao |  | 402 | 246 | 39 | 20 | 8 | 715 | pending |
| [adamabeshouse](https://github.com/adamabeshouse) | Adam Abeshouse |  | 62 | 630 | 1 | 0 | 0 | 693 | pending |
| [kalletlak](https://github.com/kalletlak) | Karthik K |  | 256 | 396 | 0 | 0 | 11 | 663 | pending |
| [ecerami](https://github.com/ecerami) |  |  | 644 | 11 | 0 | 0 | 0 | 655 | pending |
| [fedde-s](https://github.com/fedde-s) | Fedde Schaeffer | The Hyve, Utrecht (@thehyve) | 487 | 50 | 0 | 0 | 0 | 537 | pending |
| [ersinciftci](https://github.com/ersinciftci) | Ersin Ciftci |  | 366 | 82 | 0 | 0 | 0 | 448 | pending |
| [pvannierop](https://github.com/pvannierop) | Pim van Nierop | The Hyve | 156 | 272 | 6 | 0 | 2 | 436 | pending |
| [armish](https://github.com/armish) | B. Arman Aksoy |  | 315 | 0 | 0 | 0 | 0 | 315 | pending |
| [zainasir](https://github.com/zainasir) | Zain Nasir |  | 106 | 66 | 83 | 1 | 2 | 258 | pending |
| [gblaih](https://github.com/gblaih) | Bryan Lai |  | 16 | 183 | 0 | 1 | 4 | 204 | pending |
| [pieterlukasse](https://github.com/pieterlukasse) |  |  | 190 | 10 | 0 | 0 | 0 | 200 | pending |
| [sheridancbio](https://github.com/sheridancbio) | Robert Sheridan | Memorial Sloan Kettering Cancer Center | 171 | 5 | 1 | 14 | 0 | 191 | pending |
| [oplantalech](https://github.com/oplantalech) | Oleguer Plantalech | @thehyve | 108 | 72 | 0 | 4 | 2 | 186 | pending |
| [leexgh](https://github.com/leexgh) | Xiang Li |  | 16 | 143 | 0 | 0 | 0 | 159 | pending |
| [mandawilson](https://github.com/mandawilson) | Manda Wilson | Memorial Sloan-Kettering Cancer Center | 71 | 1 | 0 | 0 | 87 | 159 | pending |
| [zheins](https://github.com/zheins) | Zachary Heins |  | 157 | 0 | 0 | 0 | 0 | 157 | pending |
| [haynescd](https://github.com/haynescd) | Charles Haynes |  | 78 | 39 | 5 | 19 | 0 | 141 | pending |
| [Luke-Sikina](https://github.com/Luke-Sikina) | Luke Sikina | Boston Children's Hospital | 61 | 54 | 3 | 0 | 2 | 120 | pending |
| [yichaoS](https://github.com/yichaoS) | Yichao Sun | Memorial Sloan Kettering Cancer Center | 100 | 15 | 0 | 0 | 0 | 115 | pending |
| [istemi-bahceci](https://github.com/istemi-bahceci) | İstemi Bahçeci |  | 109 | 0 | 0 | 0 | 0 | 109 | pending |
| [JiaoJiao123](https://github.com/JiaoJiao123) | Jiaojiao Wang |  | 97 | 1 | 0 | 0 | 0 | 98 | pending |
| [ao508](https://github.com/ao508) | ao508 |  | 90 | 5 | 0 | 0 | 1 | 96 | pending |
| [adufilie](https://github.com/adufilie) | Andrew Dufilie |  | 0 | 80 | 0 | 0 | 0 | 80 | pending |
| [nschultz-sketch](https://github.com/nschultz-sketch) |  |  | 79 | 0 | 0 | 0 | 0 | 79 | pending |
| [tmazor](https://github.com/tmazor) | Tali Mazor |  | 70 | 4 | 0 | 0 | 0 | 74 | pending |
| [JREastonMarks](https://github.com/JREastonMarks) | Jeremy R. Easton-Marks |  | 42 | 0 | 1 | 28 | 0 | 71 | pending |
| [spcar7](https://github.com/spcar7) |  |  | 69 | 0 | 0 | 0 | 0 | 69 | pending |
| [ritikakundra](https://github.com/ritikakundra) |  |  | 61 | 0 | 0 | 0 | 0 | 61 | pending |
| [nr23730](https://github.com/nr23730) | Niklas Reimer | @skfit-uni-luebeck | 49 | 1 | 6 | 5 | 0 | 61 | pending |
| [caitlinjones](https://github.com/caitlinjones) |  |  | 58 | 0 | 0 | 0 | 0 | 58 | pending |
| [rmadupuri](https://github.com/rmadupuri) | Ramya Madupuri | Memorial Sloan Kettering Cancer Center | 49 | 0 | 3 | 6 | 0 | 58 | pending |
| [tamaccount](https://github.com/tamaccount) | Tamba | Ramp & Contentwrap | 4 | 48 | 0 | 0 | 0 | 52 | pending |
| [sbabyanusha](https://github.com/sbabyanusha) |  |  | 42 | 0 | 0 | 10 | 0 | 52 | pending |
| [jagnathan](https://github.com/jagnathan) | Jag (P K Jagannathan) |  | 25 | 24 | 0 | 0 | 0 | 49 | pending |
| [morungos](https://github.com/morungos) | Stuart Watt |  | 48 | 0 | 0 | 0 | 0 | 48 | pending |
| [forus](https://github.com/forus) | Ruslan Forostianov | SE4BIO | 15 | 4 | 2 | 16 | 9 | 46 | pending |
| [averyniceday](https://github.com/averyniceday) |  |  | 39 | 2 | 0 | 0 | 0 | 41 | pending |
| [victoria34](https://github.com/victoria34) | Jing Su | Memorial Sloan Kettering Cancer Center | 20 | 18 | 0 | 0 | 0 | 38 | pending |
| [fuzhaoyuan](https://github.com/fuzhaoyuan) | Zhaoyuan (Ryan) Fu | Dana-Farber Cancer Institute | 18 | 16 | 2 | 0 | 0 | 36 | pending |
| [furkansahin](https://github.com/furkansahin) | Furkan Sahin | Ubicloud | 33 | 0 | 0 | 0 | 0 | 33 | pending |
| [qlu-cls](https://github.com/qlu-cls) |  |  | 30 | 2 | 0 | 0 | 0 | 32 | pending |
| [schultzn](https://github.com/schultzn) |  |  | 26 | 0 | 0 | 0 | 0 | 26 | pending |
| [j-hudecek](https://github.com/j-hudecek) |  |  | 24 | 0 | 0 | 0 | 0 | 24 | pending |
| [TJMKuijpers](https://github.com/TJMKuijpers) | Tim Kuijpers | The Hyve | 2 | 20 | 0 | 1 | 0 | 23 | pending |
| [brittanydionigi](https://github.com/brittanydionigi) | Brittany Dionigi | google | 22 | 0 | 0 | 0 | 0 | 22 | pending |
| [amirinenik](https://github.com/amirinenik) | Kiran Amirineni |  | 2 | 19 | 0 | 0 | 0 | 21 | pending |
| [leedonghn4](https://github.com/leedonghn4) | Dong Li |  | 20 | 0 | 0 | 0 | 0 | 20 | pending |
| [ngocnn1104](https://github.com/ngocnn1104) | Ngoc Nguyen | @welldium | 2 | 16 | 0 | 0 | 0 | 18 | pending |
| [jamesqo](https://github.com/jamesqo) | James Ko | Memorial Sloan Kettering | 10 | 0 | 1 | 7 | 0 | 18 | pending |
| [Rajat-Sirohi](https://github.com/Rajat-Sirohi) | Rajat Sirohi |  | 4 | 13 | 0 | 0 | 0 | 17 | pending |
| [jtquach1](https://github.com/jtquach1) | Joyce Quach |  | 4 | 12 | 0 | 0 | 0 | 16 | pending |
| [HectorWon](https://github.com/HectorWon) |  |  | 14 | 0 | 0 | 0 | 0 | 14 | pending |
| [lemccarthy](https://github.com/lemccarthy) |  |  | 8 | 5 | 0 | 0 | 0 | 13 | pending |
| [uklineale](https://github.com/uklineale) | Neel Kuila |  | 10 | 2 | 0 | 0 | 0 | 12 | pending |
| [ChrisWakefield](https://github.com/ChrisWakefield) | Chris Wakefield | @MD-Anderson-Bioinformatics | 8 | 4 | 0 | 0 | 0 | 12 | pending |
| [pappde](https://github.com/pappde) | Denis P | Arriboworks, LLC | 7 | 4 | 0 | 0 | 0 | 11 | pending |
| [paragomi](https://github.com/paragomi) |  |  | 10 | 0 | 0 | 0 | 0 | 10 | pending |
| [priti88](https://github.com/priti88) | Priti Kumari | Dana Farber Cancer Institute | 10 | 0 | 0 | 0 | 0 | 10 | pending |
| [rnugraha](https://github.com/rnugraha) | Riza Nugraha |  | 6 | 3 | 0 | 0 | 0 | 9 | pending |
| [MatthijsPon](https://github.com/MatthijsPon) | Matthijs Pon |  | 4 | 2 | 0 | 3 | 0 | 9 | pending |
| [holtgrewe](https://github.com/holtgrewe) | Manuel Holtgrewe | Medizinische Genetik Mainz, Limbach Genetics | 8 | 0 | 0 | 0 | 0 | 8 | pending |
| [msalihaltun](https://github.com/msalihaltun) | Salih Altun |  | 0 | 8 | 0 | 0 | 0 | 8 | pending |
| [dionnezaal](https://github.com/dionnezaal) |  |  | 8 | 0 | 0 | 0 | 0 | 8 | pending |
| [artgoldberg](https://github.com/artgoldberg) | Arthur P Goldberg | Arthur Goldberg Consulting, LLC | 7 | 0 | 0 | 0 | 0 | 7 | pending |
| [Nelliney](https://github.com/Nelliney) | Tetiana |  | 0 | 7 | 0 | 0 | 0 | 7 | pending |
| [dubincorey](https://github.com/dubincorey) | Corey Dubin |  | 0 | 7 | 0 | 0 | 0 | 7 | pending |
| [rishisulakhe](https://github.com/rishisulakhe) | Rishi Prasad Sulakhe |  | 1 | 6 | 0 | 0 | 0 | 7 | pending |
| [hweej](https://github.com/hweej) | Jason Hwee |  | 4 | 3 | 0 | 0 | 0 | 7 | pending |
| [cataphract](https://github.com/cataphract) | Gustavo Lopes | @DataDog | 6 | 0 | 0 | 0 | 0 | 6 | pending |
| [johnyesit](https://github.com/johnyesit) |  |  | 0 | 6 | 0 | 0 | 0 | 6 | pending |
| [Beking0912](https://github.com/Beking0912) |  |  | 1 | 5 | 0 | 0 | 0 | 6 | pending |
| [juleskers](https://github.com/juleskers) | Jules Kerssemakers |  | 6 | 0 | 0 | 0 | 0 | 6 | pending |
| [arishta](https://github.com/arishta) | Arishta Jain |  | 1 | 4 | 0 | 0 | 0 | 5 | pending |
| [Pradyuman-aviator](https://github.com/Pradyuman-aviator) | DevPradyumansh. | NIT Hamirpur | 5 | 0 | 0 | 0 | 0 | 5 | pending |
| [agarwalrounak](https://github.com/agarwalrounak) | Rounak Agarwal |  | 2 | 3 | 0 | 0 | 0 | 5 | pending |
| [sowmiyaa-kumar](https://github.com/sowmiyaa-kumar) | Sowmiyaa Kumar |  | 4 | 1 | 0 | 0 | 0 | 5 | pending |
| [tlangs](https://github.com/tlangs) | Trevyn Langsford | Layer Health | 5 | 0 | 0 | 0 | 0 | 5 | pending |
| [i-am-leslie](https://github.com/i-am-leslie) | Leslie |  | 2 | 2 | 0 | 0 | 0 | 4 | pending |
| [kojix2](https://github.com/kojix2) |  |  | 1 | 0 | 3 | 0 | 0 | 4 | pending |
| [jfkonecn](https://github.com/jfkonecn) | John Konecny |  | 1 | 3 | 0 | 0 | 0 | 4 | pending |
| [aditygrg2](https://github.com/aditygrg2) | Aditya Garg |  | 0 | 4 | 0 | 0 | 0 | 4 | pending |
| [coderrsid](https://github.com/coderrsid) | Siddhant Sehgal |  | 0 | 4 | 0 | 0 | 0 | 4 | pending |
| [jxu8](https://github.com/jxu8) |  |  | 0 | 4 | 0 | 0 | 0 | 4 | pending |
| [alexsigaras](https://github.com/alexsigaras) | Alexandros Sigaras | Weill Cornell Medicine | 4 | 0 | 0 | 0 | 0 | 4 | pending |
| [egarcialara](https://github.com/egarcialara) | Elena |  | 4 | 0 | 0 | 0 | 0 | 4 | pending |
| [YusufZiyaOzgul](https://github.com/YusufZiyaOzgul) |  |  | 0 | 3 | 0 | 0 | 0 | 3 | pending |
| [bemijonathan](https://github.com/bemijonathan) | Jonathan Atiene | @Hive-Science | 0 | 3 | 0 | 0 | 0 | 3 | pending |
| [aderidder](https://github.com/aderidder) | Sander de Ridder |  | 3 | 0 | 0 | 0 | 0 | 3 | pending |
| [Spenca](https://github.com/Spenca) | Spencer Vatrt-Watts | @QryptInc | 3 | 0 | 0 | 0 | 0 | 3 | pending |
| [olzhasmukayev](https://github.com/olzhasmukayev) | Olzhas Mukayev |  | 0 | 3 | 0 | 0 | 0 | 3 | pending |
| [Leowisd](https://github.com/Leowisd) | Yifu |  | 0 | 3 | 0 | 0 | 0 | 3 | pending |
| [ugurdogrusoz](https://github.com/ugurdogrusoz) |  |  | 3 | 0 | 0 | 0 | 0 | 3 | pending |
| [FlorisVleugels](https://github.com/FlorisVleugels) | Melrus |  | 1 | 2 | 0 | 0 | 0 | 3 | pending |
| [khaledfahmy123](https://github.com/khaledfahmy123) | Khaled Fahmy | None | 0 | 3 | 0 | 0 | 0 | 3 | pending |
| [sambrightman](https://github.com/sambrightman) | Sam Brightman |  | 3 | 0 | 0 | 0 | 0 | 3 | pending |
| [fkaercher](https://github.com/fkaercher) | Florian Kaercher |  | 3 | 0 | 0 | 0 | 0 | 3 | pending |
| [Djokovic0311](https://github.com/Djokovic0311) | Jiahang Li |  | 2 | 1 | 0 | 0 | 0 | 3 | pending |
| [kunalhemnani1](https://github.com/kunalhemnani1) | Kunal Hemnani |  | 0 | 2 | 0 | 0 | 0 | 2 | pending |
| [ayushns9](https://github.com/ayushns9) | Ayush Goel | Stripe | 0 | 2 | 0 | 0 | 0 | 2 | pending |
| [saurabhhhcodes](https://github.com/saurabhhhcodes) | Saurabh Kumar Bajpai | Akoode Technologies | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [marriott-er](https://github.com/marriott-er) |  |  | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [pozhidaevak](https://github.com/pozhidaevak) | Anton Pozhidaev |  | 1 | 1 | 0 | 0 | 0 | 2 | pending |
| [brettvanderwerff](https://github.com/brettvanderwerff) | Brett Vanderwerff |  | 0 | 2 | 0 | 0 | 0 | 2 | pending |
| [SURAJ-SHARMA27](https://github.com/SURAJ-SHARMA27) | SURAJ |  | 0 | 2 | 0 | 0 | 0 | 2 | pending |
| [KingAlex1985](https://github.com/KingAlex1985) |  |  | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [SAHU-01](https://github.com/SAHU-01) | Ankita Sahu | ZkAGI | 0 | 2 | 0 | 0 | 0 | 2 | pending |
| [ckandoth](https://github.com/ckandoth) | Cyriac Kandoth | Penn Medicine | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [dianab0](https://github.com/dianab0) |  |  | 1 | 1 | 0 | 0 | 0 | 2 | pending |
| [lllinging](https://github.com/lllinging) |  |  | 0 | 2 | 0 | 0 | 0 | 2 | pending |
| [amanbhardwaj12072003](https://github.com/amanbhardwaj12072003) | Aman Bhardwaj |  | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [ugurkoysuren](https://github.com/ugurkoysuren) | Ugur Koysuren |  | 1 | 0 | 1 | 0 | 0 | 2 | pending |
| [sayan-aiml](https://github.com/sayan-aiml) | Sayan Kr. Pattanayak |  | 0 | 2 | 0 | 0 | 0 | 2 | pending |
| [kurt-mueller-osumc](https://github.com/kurt-mueller-osumc) | Kurt Mueller | The Ohio State University College of Medicine Research IT | 1 | 0 | 1 | 0 | 0 | 2 | pending |
| [dtenenba](https://github.com/dtenenba) | Dan Tenenbaum | @FredHutch SciComp | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [VenkateshVishwas](https://github.com/VenkateshVishwas) | Venky |  | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [johnyaku](https://github.com/johnyaku) | John Reeves |  | 1 | 0 | 1 | 0 | 0 | 2 | pending |
| [VarshiniGunti](https://github.com/VarshiniGunti) | Varshini | Indian institute of technology Bhilai | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [siddhiguptas](https://github.com/siddhiguptas) | Siddhi Gupta |  | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [tweep](https://github.com/tweep) | Jan-Hinnerk Vogel | Open to new opportunities | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [vaibhavlachhwani](https://github.com/vaibhavlachhwani) | Vaibhav Lachhwani |  | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [gritsynad](https://github.com/gritsynad) | Gritsyna Dmitriy |  | 2 | 0 | 0 | 0 | 0 | 2 | pending |
| [gautamsarawagi](https://github.com/gautamsarawagi) | Gautam Sarawagi |  | 0 | 2 | 0 | 0 | 0 | 2 | pending |
| [tonatiuh-gonzalez47](https://github.com/tonatiuh-gonzalez47) | Tonatiuh Gonzalez |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [scvannost](https://github.com/scvannost) | SC Van Nostrand |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [eugeniomazzone](https://github.com/eugeniomazzone) | Eugenio Mazzone | University of Turin | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [KhushamBansal](https://github.com/KhushamBansal) | Khusham Bansal |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [aswin2108](https://github.com/aswin2108) | Aswin Shailajan | Vellore Institute of Technology | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [m12m3r](https://github.com/m12m3r) | Mark Shehata |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [Vignesh-JavaDev](https://github.com/Vignesh-JavaDev) |  |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [viveak910](https://github.com/viveak910) | viveak |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [scbaysal](https://github.com/scbaysal) |  |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [jorvis](https://github.com/jorvis) | Joshua Orvis | Institute for Genome Sciences | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [er-abhijeet](https://github.com/er-abhijeet) | Abhijeet M |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [PerVillalva](https://github.com/PerVillalva) | Percival Villalva |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [mhsh312](https://github.com/mhsh312) |  |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [karissawhiting](https://github.com/karissawhiting) |  |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [Gautam-aman](https://github.com/Gautam-aman) | Aman Gautam |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [gulshan2052](https://github.com/gulshan2052) | Gulshan Anand |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [callachennault](https://github.com/callachennault) | Calla Chennault |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [manik-dhanjal](https://github.com/manik-dhanjal) | Manik Dhanjal | Escorts Kubota Limited | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [YashhCanCode](https://github.com/YashhCanCode) | Yashwanth Konnuru | Marri Laxman Reddy of institute of technology and management | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [pambot](https://github.com/pambot) | Pambot | Shopify | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [Injora](https://github.com/Injora) | Injora |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [hskarlupka](https://github.com/hskarlupka) | Heath Skarlupka |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [sanki92](https://github.com/sanki92) | Sankalp Tripathi |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [pcvolkmer](https://github.com/pcvolkmer) | Paul-Christian Volkmer |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [gorkemsolun](https://github.com/gorkemsolun) | Görkem Kadir Solun | ETH Zürich | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [Zohaibarif69](https://github.com/Zohaibarif69) | ZOHAIB |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [Aiosa](https://github.com/Aiosa) |  |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [officialasishkumar](https://github.com/officialasishkumar) | Asish Kumar |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [rohangoel96](https://github.com/rohangoel96) | Rohan Goel |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [zeynepkaragoz](https://github.com/zeynepkaragoz) | Zeynep Karagoz, PhD | @thehyve | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [RyukXO-code](https://github.com/RyukXO-code) | Sagnik |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [teesamuel](https://github.com/teesamuel) | Samuel Olufemi | Silverrail Technology | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [agandolf](https://github.com/agandolf) |  |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [justinjao](https://github.com/justinjao) | Justin Jao |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [anthony-cros](https://github.com/anthony-cros) | Anthony Cros | Software architect | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [rishav-raj-genx](https://github.com/rishav-raj-genx) | Rishav Raj |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [gauravbyte](https://github.com/gauravbyte) | Gaurav Chaudhari | IIT Madras CSE | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [Annu881](https://github.com/Annu881) |  |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [thomasmarwitz](https://github.com/thomasmarwitz) |  |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [mdhvprasad](https://github.com/mdhvprasad) | mvprasad |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [NikdAK](https://github.com/NikdAK) | Niklas dAK | Technical University of Munich (TUM) | 0 | 0 | 1 | 0 | 0 | 1 | pending |
| [anshuman-rai-27](https://github.com/anshuman-rai-27) | Anshuman Rai | @soundversegit | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [nbentoneves](https://github.com/nbentoneves) | Nuno Bento |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [meow1729](https://github.com/meow1729) | Prophet_MEOW |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [jochemb](https://github.com/jochemb) | Jochem Bijlard |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [yashhash2](https://github.com/yashhash2) | Yash Kumar Singh |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [stevearmstrong-dev](https://github.com/stevearmstrong-dev) | Steve Armstrong |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [Rgtemze](https://github.com/Rgtemze) | Ziya ERKOC |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [thepiyush-303](https://github.com/thepiyush-303) | Piyush Bhatt |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [mervekilicarslan5](https://github.com/mervekilicarslan5) | Merve Kılıçarslan | @TUM | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [pnartowski](https://github.com/pnartowski) | Nartowski Paweł |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [kunalchandan](https://github.com/kunalchandan) | Kunal Chandan | MicroAlchemy Inc. @microAlchemy | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [waffle-iron](https://github.com/waffle-iron) | Making GitHub Delicious. | Rally Software | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [saxenanurag](https://github.com/saxenanurag) | Anurag Saxena | Cleveland Clinic Research | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [FilledEther20](https://github.com/FilledEther20) | Chaitanya Gairola |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [Player256](https://github.com/Player256) | space_samurai |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [khzhu](https://github.com/khzhu) | Kelsey Zhu |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [ShahKirtan2003](https://github.com/ShahKirtan2003) | Kirtan Shah |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [Vinny02](https://github.com/Vinny02) |  |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [ruslan-forostianov](https://github.com/ruslan-forostianov) | Ruslan Forostianov |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [eliaslautensack](https://github.com/eliaslautensack) |  |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [Ak-Macha](https://github.com/Ak-Macha) | Ak-Matcha |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [emmanuel-ferdman](https://github.com/emmanuel-ferdman) | Emmanuel Ferdman |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [heuermh](https://github.com/heuermh) | Michael L Heuer | Stealth-Mode Biotech | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [calvinlu3](https://github.com/calvinlu3) | Calvin Lu |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [stachnim](https://github.com/stachnim) | Marcin Stachniuk |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [GarvitDadheech](https://github.com/GarvitDadheech) | Garvit Dadheech |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [Ismael-Sallami](https://github.com/Ismael-Sallami) | Ismael Sallami |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [MizeroR](https://github.com/MizeroR) | Reine Mizero |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [chandrikarj](https://github.com/chandrikarj) | Chandrika |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [rosh2525](https://github.com/rosh2525) | Roshan | IIT Jodhpur | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [HarshithaSivalingala](https://github.com/HarshithaSivalingala) | Sai Harshitha Sivalingala |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [jCHENEBY](https://github.com/jCHENEBY) |  | UIO Oslo, Elixir Norway | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [scarrero4660](https://github.com/scarrero4660) |  |  | 0 | 1 | 0 | 0 | 0 | 1 | pending |
| [sandertan](https://github.com/sandertan) | Sander Tan |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [chiang-sh](https://github.com/chiang-sh) | Shan Chiang |  | 1 | 0 | 0 | 0 | 0 | 1 | pending |
| [jonkiky](https://github.com/jonkiky) | Yizhen Chen |  | 0 | 0 | 0 | 0 | 1 | 1 | pending |
| [sdpetrides](https://github.com/sdpetrides) | Stephen Petrides | @nadeemlab | 0 | 0 | 0 | 0 | 1 | 1 | pending |
| [sgicbpc](https://github.com/sgicbpc) |  |  | 0 | 0 | 0 | 1 | 0 | 1 | pending |
| [codyharoldsen](https://github.com/codyharoldsen) |  |  | 0 | 0 | 0 | 0 | 1 | 1 | pending |
