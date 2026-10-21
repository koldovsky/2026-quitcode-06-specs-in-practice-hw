# Здача WS6

## Дані

- Роль: pm
- Команда: therapy-scheduling
- GitHub-логін: Sofiia-pm
- Ваше репо: https://github.com/Sofiia-pm/therapy-scheduling-spec
- SHA: b2126030318fa9eec367cee43a08abb4033de110
- Репо вимог PM: https://github.com/Sofiia-pm/therapy-scheduling-spec
- Прод-URL: —

## PM

- Сховище вимог: issues
- Продукт: https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/1
- Вимоги першого зрізу: https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/2
- Самоперевірка за чеклістом: https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/2#issuecomment-6256345360
- Питання, на які ви відповіли: зі зміною вимоги — https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/3, https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/4, https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/5, https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/6, https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/7, https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/8, https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/9, https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/10, https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/11, https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/12; після строку змін, «у наступному оновленні (WS7)» — https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/13, https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/14, https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/15
- Зміни вимог із журналом змін: «Журнал змін» вимоги https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/2; коментарі «Зміна: …» — https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/2#issuecomment-6267630481, https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/2#issuecomment-6269417413, https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/2#issuecomment-6289030291, https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/1#issuecomment-6255756879, https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/1#issuecomment-6256334914

## Нотатка PM — порівняння реалізацій (трек D)

Порівнювала 3 реалізації за їхніми `docs/conformance.md` і `docs/spec-reading.md`. Від двох розробників реалізацій на 21.10 не отримано — додам, коли надішлють.

- HryhoriiHaponiukQuitCode (знімок 19.10): https://github.com/HryhoriiHaponiukQuitCode/therapy-scheduling/blob/main/docs/conformance.md, https://github.com/HryhoriiHaponiukQuitCode/therapy-scheduling/blob/main/docs/spec-reading.md
- maryan-qc (знімок 21.10): https://github.com/maryan-qc/therapy-scheduling/blob/main/docs/conformance.md, https://github.com/maryan-qc/therapy-scheduling/blob/main/docs/spec-reading.md
- markkern-hyra (знімок 21.10): https://github.com/markkern-hyra/therapy-scheduling/blob/main/docs/conformance.md, https://github.com/markkern-hyra/therapy-scheduling/blob/main/docs/spec-reading.md

1. AC / вимога: AC-HOLD-09 — розклад терапевта. Як прочитали чи реалізували: HryhoriiHaponiukQuitCode — утримання й сеанси на 7 днів від сьогодні (власне припущення); maryan-qc — тиждень понеділок–неділя з усіма слотами й статусами, з перемиканням тижнів. Чому: у вимозі не було ні періоду, ні вмісту розкладу; ознаку успіху «на тиждень» прочитали по-різному, а глосарій («Розклад» — лише утримання й сеанси) суперечив AC-HOLD-21 («слот показано як вільний»). Що зробив PM: відповіла в #9 (тиждень пн–нд + усі слоти зі статусами), додала AC-HOLD-30, 31, а уточнення «Розклад» у глосарії, обіцяне в #9, не збереглося — розробник помітив розбіжність між відповіддю й знімком; виправлю в оновленні для WS7. Висновок: період і вміст екрана треба задавати критерієм, а не лише ознакою успіху. Посилання: https://github.com/HryhoriiHaponiukQuitCode/therapy-scheduling/blob/main/src/app/%28app%29/my-schedule/data.ts, https://github.com/maryan-qc/therapy-scheduling/blob/main/src/lib/holds/schedule.ts
2. AC / вимога: AC-HOLD-20 — список утримань планувальника. Як прочитали чи реалізували: maryan-qc показує «Held», «Confirmed» і «Expired» (висновок із матриці прав); HryhoriiHaponiukQuitCode — окремо лише прострочені утримання; pavmys спитав окремо (#15). Чому: критерії описували тільки прострочені утримання, а що ще в списку і в якому порядку — ні. Що зробив PM: відповіла в #15 — лише «Held» і «Expired», за часом слоту від найближчого; зміна у вимозі — у наступному оновленні (WS7). Посилання: https://github.com/maryan-qc/therapy-scheduling/blob/main/src/app/holds/page.tsx, https://github.com/HryhoriiHaponiukQuitCode/therapy-scheduling/blob/main/src/lib/slots.ts
3. AC / вимога: AC-HOLD-06 і AC-HOLD-07 — слоти, що вже почалися. Як прочитали чи реалізували: maryan-qc спершу показував минулі слоти як вільні (тимчасовий варіант A), після відповіді — окремий статус «Past»; HryhoriiHaponiukQuitCode трактує «почався» з хвилини початку включно (власне припущення). Чому: суперечність у вимозі — за AC-HOLD-06 прострочений слот «знову вільний», а за AC-HOLD-07 слот, що почався, утримати не можна. Що зробив PM: відповіла в #10 — статус «Past», такі слоти не вільні й не рахуються для «No free slots on this day.»; додала AC-HOLD-32, 33 і припущення про межу «з моменту початку включно». Посилання: https://github.com/maryan-qc/therapy-scheduling/blob/main/src/lib/holds/status.ts, https://github.com/HryhoriiHaponiukQuitCode/therapy-scheduling/blob/main/docs/spec-reading.md
4. AC / вимога: AC-HOLD-11, 15 — «коректний email». Як прочитали чи реалізували: кожен розробник визначив правило сам (maryan-qc — рівно один «@», непорожні частини, без пробілів усередині). Чому: «valid email» — розмите формулювання з одним прикладом (без «@»). Що зробив PM: на 21.10 не уточнено; у WS7 додам точне правило в «Припущення». Окремо: для регістру й пробілів відповіла в #11 (AC-HOLD-34, 35). Посилання: https://github.com/maryan-qc/therapy-scheduling/blob/main/src/lib/holds/clients.ts, https://github.com/HryhoriiHaponiukQuitCode/therapy-scheduling/blob/main/src/lib/clients.ts
5. AC / вимога: AC-HOLD-27, 36 — звідки беруться планувальники. Як прочитали чи реалізували: maryan-qc узяв користувачів із `supabase/demo-users.json`; pavmys до відповіді додавав admin1, scheduler1 і scheduler2 у сид (тимчасовий план у питанні #13); markkern-hyra на 21.10 відклав AC-HOLD-27 і 36. Чому: критерії мають scheduler1 і scheduler2, а в «Припущеннях» сид — лише терапевти. Що зробив PM: відповіла в #13 — усі користувачі зрізу 1 у сиді, створення користувачів поза межами; зміна — у наступному оновленні (WS7). Посилання: https://github.com/maryan-qc/therapy-scheduling/blob/main/supabase/demo-users.json, https://github.com/Sofiia-pm/therapy-scheduling-spec/issues/13, https://github.com/markkern-hyra/therapy-scheduling/blob/main/docs/conformance.md
6. AC / вимога: обсяг і знімок вимог. Як прочитали чи реалізували: HryhoriiHaponiukQuitCode — знімок 19.10, 24 AC реалізовано (без AC-HOLD-25…36, доданих пізніше), AC-HOLD-18 зробив ще до моєї відповіді за власною рекомендацією; maryan-qc — знімок 21.10, усі 36 AC; markkern-hyra — знімок 21.10, 4 з 36 реалізовано, решта «відкладено», журнал `spec-reading.md` порожній. Чому: вимоги я опублікувала 19.10 замість 16.10, перший раунд питань до брифу провела письмово 19.10 замість зустрічі 13–15.10, а відповіді й нові AC з'являлися 19–20.10 — розробники синхронізувались у різний час. Що зробив PM: усі зміни — з рядком у «Журналі змін» і посиланням на питання, «вимоги оновлено» в чаті; висновок — питання до брифу збирати до написання вимог, а критерії публікувати вчасно, щоб усі стартували з одного знімка. Посилання: https://github.com/HryhoriiHaponiukQuitCode/therapy-scheduling/blob/main/docs/conformance.md, https://github.com/maryan-qc/therapy-scheduling/blob/main/docs/conformance.md, https://github.com/markkern-hyra/therapy-scheduling/blob/main/docs/conformance.md

## Розробник

- Рядок «Вимоги:» з `docs/conformance.md` на SHA: —
- Перший PR «Оновлення вимог»: —
- Журнал `docs/spec-reading.md`: —
- Питання в репо PM (щонайменше 3, з них щонайменше 1 — власне issue): —
- PR «Специфікація» з перекладом першого зрізу: —
- Зміна `impl-<зріз>`: —
- PR-и задач «Реалізація» (щонайменше 2): —
- PR «Оновлення вимог» після уточнень PM: —
- PR «Специфікація» зі змінами після уточнень: —
- AC, які ви реалізували: —

## Бонус E

—
